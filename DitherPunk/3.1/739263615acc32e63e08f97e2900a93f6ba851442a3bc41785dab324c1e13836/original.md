```
ErrorDiffusion(filter, offset)
```

Generalized error diffusion algorithm. When calling `dither` using a color palette `cs`, this will iterate over pixels and round them to the closest color in `cs`. The rounding error is then "diffused" over the neighborhood defined by the matrix `filter` centered around an integer `offset`.

When using `dither` or `dither!` with an ErrorDiffusion method, the keyword argument `clamp_error` can be passed, which defaults to `true`. When `true`, the accumulated error on each pixel is clamped within limits of the image's colorant type before looking up the closest color. Setting `clamp_error=false` might be desired to achieve a glitchy effect.

# Example

```julia-repl
julia> alg = FloydSteinberg() # returns ErrorDiffusion instance
ErrorDiffusion{Rational{Int64}, UnitRange{Int64}}(CartesianIndex{2}[CartesianIndex(1, 0), CartesianIndex(-1, 1), CartesianIndex(0, 1), CartesianIndex(1, 1)], Rational{Int64}[7//16, 3//16, 5//16, 1//16], (-1:1, 0:1))

julia> cs = ColorSchemes.PuOr_7  # using ColorSchemes.jl for color palette presets

julia> dither(img, alg, cs)

julia> dither(img, alg, cs; clamp_error=false)
```
