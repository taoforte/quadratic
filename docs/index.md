# Teaching Python Basics with Quadratic Equations & Real-Life Problems

## Lesson Plan Overview

### Target Audience
- Two 16-year-olds with basic math knowledge
- No prior programming experience required
- Focus on practical applications

## Session 1: Python Fundamentals & Quadratic Basics

### 1.1 Why Python?
```python
# Simple introduction
print("Hello, Python World!")
print("We can solve math problems easily!")
```

### 1.2 Basic Python Operations
```python
# Basic math operations
a = 5
b = 3
print("Addition:", a + b)
print("Multiplication:", a * b)
print("Power:", a ** 2)  # squared
```

### 1.3 Quadratic Equation Refresher
**Standard form:** ax² + bx + c = 0  
**Solutions:** x = [-b ± √(b² - 4ac)] / 2a

```python
# Let's code the quadratic formula step by step
import math

def quadratic_formula(a, b, c):
    discriminant = b**2 - 4*a*c
    
    if discriminant < 0:
        return "No real solutions"
    
    x1 = (-b + math.sqrt(discriminant)) / (2*a)
    x2 = (-b - math.sqrt(discriminant)) / (2*a)
    
    return x1, x2

# Test with a simple equation: x² - 5x + 6 = 0
print(quadratic_formula(1, -5, 6))  # Should give (3, 2)
```

## Session 2: Real-Life Problem 1 - Projectile Motion

### The Physics Behind It
- A ball thrown upward follows a parabolic path
- Equation: h(t) = -½gt² + v₀t + h₀
- Where: g = gravity, v₀ = initial velocity, h₀ = initial height

```python
def projectile_motion():
    print("=== PROJECTILE MOTION CALCULATOR ===")
    
    # Get user input
    initial_velocity = float(input("Enter initial velocity (m/s): "))
    initial_height = float(input("Enter initial height (m): "))
    gravity = 9.8  # m/s²
    
    # Our equation: h(t) = -4.9t² + v₀t + h₀
    # When ball hits ground: h(t) = 0
    # So: -4.9t² + v₀t + h₀ = 0
    
    a = -4.9
    b = initial_velocity
    c = initial_height
    
    solutions = quadratic_formula(a, b, c)
    
    if isinstance(solutions, tuple):
        # We want the positive time value
        time_to_ground = max(solutions)
        max_height_time = -b / (2*a)  # Time at maximum height
        max_height = a * max_height_time**2 + b * max_height_time + c
        
        print(f"\nResults:")
        print(f"Time to hit ground: {time_to_ground:.2f} seconds")
        print(f"Maximum height: {max_height:.2f} meters")
        print(f"Time at max height: {max_height_time:.2f} seconds")
    else:
        print("The projectile never hits the ground!")

# Run the function
projectile_motion()
```

### Example Usage:
```
Input: v₀ = 20 m/s, h₀ = 1.5 m
Output: Time to hit ground ≈ 4.18 seconds, Max height ≈ 21.89 meters
```

## Session 3: Real-Life Problem 2 - Business Profit Optimization

### The Business Scenario
A lemonade stand wants to maximize profit:
- Cost to make x cups: C(x) = 0.1x² + 0.5x + 10
- Revenue from selling x cups: R(x) = 2x
- Profit: P(x) = R(x) - C(x) = -0.1x² + 1.5x - 10

```python
def profit_optimization():
    print("=== LEMONADE STAND PROFIT OPTIMIZER ===")
    
    # Profit function: P(x) = -0.1x² + 1.5x - 10
    # To find break-even points: P(x) = 0
    # To find maximum profit: derivative = 0
    
    a = -0.1
    b = 1.5
    c = -10
    
    # Find break-even points
    break_even_points = quadratic_formula(a, b, c)
    
    if isinstance(break_even_points, tuple):
        low, high = sorted(break_even_points)
        print(f"Break-even points: {low:.0f} cups and {high:.0f} cups")
        
        # Maximum profit occurs at vertex
        optimal_cups = -b / (2*a)
        max_profit = a * optimal_cups**2 + b * optimal_cups + c
        
        print(f"\nOptimal production: {optimal_cups:.0f} cups")
        print(f"Maximum profit: ${max_profit:.2f}")
        
        # Show profit at different quantities
        print("\nProfit at different production levels:")
        for cups in [10, 15, 20, 25, 30]:
            profit = a * cups**2 + b * cups + c
            print(f"{cups} cups: ${profit:.2f}")

profit_optimization()
```

## Session 4: Real-Life Problem 3 - Sports Analytics

### Basketball Shot Analysis
A basketball shot follows a parabolic path. Let's analyze if a shot will go in!

```python
def basketball_shot_analyzer():
    print("=== BASKETBALL SHOT ANALYZER ===")
    
    # Scenario: Player shoots from 20 feet, release height = 7 feet
    # Basket height = 10 feet, distance to basket = 20 feet
    # Perfect arc equation: y = -0.02x² + 0.7x + 7
    
    shot_distance = float(input("Enter shot distance (feet): "))
    release_height = float(input("Enter release height (feet): "))
    
    # We'll assume a nice arc: y = ax² + bx + c
    # Where a determines the steepness of the arc
    a = -0.02  # Negative for downward opening parabola
    b = 0.7    # Controls the initial upward trajectory
    c = release_height
    
    # Check if the ball goes through the hoop at x = shot_distance, y = 10 feet
    height_at_basket = a * shot_distance**2 + b * shot_distance + c
    basket_height = 10
    
    print(f"\nShot Analysis:")
    print(f"Height when reaching basket: {height_at_basket:.2f} feet")
    
    # Basketball rim diameter is 18 inches, so we have some tolerance
    if 9.5 <= height_at_basket <= 10.5:
        print("🎯 PERFECT SHOT! Swish!")
    elif 9.0 <= height_at_basket <= 11.0:
        print("✅ Good shot! Might go in with a bounce.")
    else:
        print("❌ Poor trajectory. Unlikely to score.")
    
    # Find maximum height of shot
    max_height_x = -b / (2*a)
    max_height = a * max_height_x**2 + b * max_height_x + c
    print(f"Maximum shot height: {max_height:.2f} feet")

basketball_shot_analyzer()
```

## Session 5: Interactive Challenge - Design Your Own Problem

### Template for Students to Create Their Own Scenarios
```python
def create_your_own_problem():
    print("=== CREATE YOUR OWN QUADRATIC PROBLEM ===")
    
    print("Think of a real-life situation that follows a parabolic pattern!")
    print("Examples:")
    print("- Rocket launch trajectory")
    print("- Bridge arch design")
    print -("- Profit optimization for a business")
    
    # Student inputs their scenario
    scenario = input("\nDescribe your scenario: ")
    a = float(input("Enter 'a' coefficient: "))
    b = float(input("Enter 'b' coefficient: "))
    c = float(input("Enter 'c' coefficient: "))
    
    print(f"\nYour equation: y = {a}x² + {b}x + {c}")
    
    # Analyze their equation
    solutions = quadratic_formula(a, b, c)
    
    if isinstance(solutions, tuple):
        x1, x2 = solutions
        print(f"Roots/x-intercepts: {x1:.2f} and {x2:.2f}")
        
        # Find vertex (maximum/minimum)
        vertex_x = -b / (2*a)
        vertex_y = a * vertex_x**2 + b * vertex_x + c
        
        if a > 0:
            print(f"Minimum point at ({vertex_x:.2f}, {vertex_y:.2f})")
        else:
            print(f"Maximum point at ({vertex_x:.2f}, {vertex_y:.2f})")
        
        # Let them interpret what this means in their scenario
        print("\nWhat do these values mean in your scenario?")
        print("Discuss with your partner!")

create_your_own_problem()
```

## Learning Outcomes

### Python Concepts Covered:
- Variables and basic math operations
- Functions and parameters
- User input/output
- Conditional statements (if/else)
- Importing and using modules

### Math Concepts Reinforced:
- Quadratic equations and solutions
- Discriminant and nature of roots
- Vertex of parabola (max/min points)
- Real-world applications of algebra

### Critical Thinking Skills:
- Translating word problems into equations
- Interpreting mathematical results in context
- Problem-solving with multiple approaches
- Creative application of mathematical concepts

## Teaching Tips

1. **Start with concrete examples** they can visualize (sports, games)
2. **Use lots of print statements** to see what's happening
3. **Encourage experimentation** - change numbers and see what happens
4. **Pair programming** - one types, one reviews and suggests
5. **Relate to their interests** - sports, video games, money

 