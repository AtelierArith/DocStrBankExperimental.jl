```
hspan(y)
```

Draw a rectangle between the horizontal line at position `y[1]` and the horizontal line at position `y[2]`. If `length(y) ≥ 4`, then further rectangles are drawn between `y[3]` and `y[4]`, `y[5]` and `y[6]`, and so on. If `length(y)` is odd, then the last entry of `y` is ignored.

# Example

```julia-repl
julia> hspan(1:6)
```
