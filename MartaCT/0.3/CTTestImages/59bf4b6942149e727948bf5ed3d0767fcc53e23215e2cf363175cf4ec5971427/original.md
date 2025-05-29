```
circle_polar_image([T=Float32] nr, nϕ, radius; value=1) where {T}
```

Create a circle of radius `radius` inside a `nr×nϕ` image in polar coordinates .

# Examples

```julia-repl
julia> circle_polar_image(30, 30, 10)
30×30 Array{Float32,2}:
[...]
```
