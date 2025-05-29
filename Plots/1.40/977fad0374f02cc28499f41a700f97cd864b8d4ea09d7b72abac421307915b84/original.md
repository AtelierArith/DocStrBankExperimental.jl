```
vspan(x)
```

Draw a rectangle between the vertical line at position `x[1]` and the vertical line at position `x[2]`. If `length(x) ≥ 4`, then further rectangles are drawn between `x[3]` and `x[4]`, `x[5]` and `x[6]`, and so on. If `length(x)` is odd, then the last entry of `x` is ignored.

# Example

```julia-repl
julia> vspan(1:6)
```
