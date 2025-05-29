An LSystem, or Lindenmayer system, is a set of rules that can define recursive patterns.

You can define an L-System like this:

```
koch = LSystem(["F" => "F+F--F+F"], "F")
```

and use Luxor to draw it like this:

```
drawLSystem(koch, forward=30, turn=45, iterations=6)
```

See `help?> LSystem` and `help?> ?>LSystem` for more.
