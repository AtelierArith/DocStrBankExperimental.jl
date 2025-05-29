A Lindenmayer system is a set of rules that can build recursive patterns. In Lindenmayer.jl, an LSystem structure consists of:

  * Rules: a set of search and replace strings
  * Seed: a string that defines the initial state for the system
  * State: the current state (initially empty, added when the system is evaluated)

You can define an L-System like this:

```
using Lindenmayer
koch = LSystem(["F" => "F+F--F+F"], "F")
```

This says: there's just one rule; search for "F" and replace with "F+F–F+F" for each iteration. The starting "seed" is the initial state consisting of just a single "F".

# Extended help

To draw the LSystem we use Luxor.jl's Turtle, which interprets the characters in the rule as instructions or commands. For example, "F" converts to `Luxor.Forward()``, "+" rotates clockwise, "-" rotates counterclockwise, and so on.

```
drawLSystem(LSystem(["F" => "5F+F--F+Ftt"], "F"),
    startingx = -400,
    forward = 4,
    turn = 80,
    iterations = 6)
```

Keyword options for `drawLSystem` include:

```
forward=15,
turn=45,
iterations=6,
filename="/tmp/lsystem.pdf",
width=1000,
height=1000,
startingpen=(0.3, 0.6, 0.8), # starting color RGB
startingx=0,
startingy=0,
startingorientation=0,
showpreview=true
```

The following characters are recognized in LSystem rules.

F - step Forward

G - same as F

B - step backwards

V - same as B

f - half a step forward

b - turn 180° and take half a step forward

U - lift the pen (stop drawing)

D - pen down (start drawing)

`+` - turn by angle

`-` - turn backwards by angle

r - turn randomly by 10° 15° 30° 45° or 60°

T - change the hue at random

t - shift the hue by 5°

c - randomize the saturation

O - choose a random opacity value

l - increase the step size by 1

s - decrease the step size by 1

5 - set line width to 5

4 - set line width to 4

3 - set line width to 3

2 - set line width to 2

1 - set line width to 1

n - set line width to 0.5

o - draw a circle with radius step/4

q - draw a square with side length step/4

`@` - turn 5°

`&` - turn -5°

[ - push the current state on the stack

] - pop the current state off the stack

`*` - execute the arbitrary function passed as `asteriskfunction()` ```
