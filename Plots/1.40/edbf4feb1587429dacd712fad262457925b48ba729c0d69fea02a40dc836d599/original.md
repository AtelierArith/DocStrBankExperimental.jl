```
contour(x,y,z)
contour!(x,y,z)
```

Draw contour lines of the surface `z`.

# Arguments

  * `levels`: Contour levels (if `AbstractVector`) or number of levels (if `Integer`)
  * `fill`: Bool. Fill area between contours or draw contours only (false by default)

# Example

```julia-repl
julia> x = y = range(-20, stop = 20, length = 100)
julia> contour(x, y, (x, y) -> x^2 + y^2)
```
