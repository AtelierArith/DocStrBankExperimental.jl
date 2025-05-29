```
square_image([T=Float32] r, c; l=nothing) where {T}
```

Create a `l×l` square inside a `r×c` image.

# Examples

```julia-repl
julia> square_image(30, 30; l=10)
30×30 Array{Float32,2}:
[...]
```
