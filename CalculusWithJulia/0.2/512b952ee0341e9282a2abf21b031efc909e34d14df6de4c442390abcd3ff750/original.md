```
secant(f::Function, a, b)
```

Returns a function describing the secant line to the graph of `f` at `x=a` and `x=b`.

Example. Where does the secant line intersect the `y` axis?

```
f(x) = sin(x)
a, b = pi/4, pi/3
sl = secant(f, a, b)  # or sl(x) = secant(f, a, b)(x) to use a generic function
sl(0)
```
