```
circle_image([T=Float32]; radius=20, value=1) where {T}
```

Create a square image with a circle of given value.

# Examples

```julia-repl
julia> circle_image(30, 0.8)
30×30 Array{Float32,2}:
[...]
```

See also: [`gray_scale_image`](@ref), [`combine_images`](@ref)
