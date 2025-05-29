```
gray_scale_image(
    [T=Float32];
    rows=40,
    cols=200,
    swidth=nothing,
    sheight=nothing,
    gray_scale=-1000..1000,
) where {T}
```

Create an image with a gray scale rectangle with given scale gray_scale.

# Examples

```julia-repl
julia> gray_scale_image(swidth=80, sheight=40, gray_scale=-1000..1000)
40×80 Array{Float32,2}:
[...]
```

See also: [`circle_image`](@ref), [`combine_images`](@ref)
