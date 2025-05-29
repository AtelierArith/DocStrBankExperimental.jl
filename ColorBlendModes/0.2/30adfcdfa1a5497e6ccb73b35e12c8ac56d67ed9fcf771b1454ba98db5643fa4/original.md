```
blend(c1, c2; mode=BlendNormal, opacity=1, op=CompositeSourceOver)
```

Create the mixed color of two colors `c1` and `c2`. The `c1` means the backdrop color and the `c2` means the source color.

`mode` specifies the blend mode, e.g. [`BlendMultiply`](@ref).

`opacity` modifies the source (i.e. `c2`-side) alpha by multiplication.

`op` specifies the composite operations, e.g. [`CompositeSourceAtop`](@ref).

The return type is the same as `c1`.

# Examples

```jldoctest
julia> blend(RGB(1, 0.5, 0), RGB(0, 0.5, 1), mode=BlendLighten)
RGB{Float64}(1.0,0.5,1.0)
```
