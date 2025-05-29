```
tangent(f::Function, c)
```

Returns a function describing the tangent line to the graph of `f` at `x=c`.

Example. Where does the tangent line intersect the y axis?

```
f(x) = sin(x)
tl = tangent(f, pi/4)  # or tl(x) = tangent(f, pi/3)(x) to use a generic function
tl(0)
```

Uses the automatic derivative of `f` to find the slope of the tangent line at `x=c`.
