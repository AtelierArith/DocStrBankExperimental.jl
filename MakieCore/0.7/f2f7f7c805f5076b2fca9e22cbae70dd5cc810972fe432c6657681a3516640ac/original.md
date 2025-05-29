```
convert_attribute(value, attribute::Key[, plottype::Key])
```

Convert `value` into a suitable domain for use as `attribute`.

# Example

```jldoctest
julia> using Makie

julia> Makie.convert_attribute(:black, key"color"())
RGBA{Float32}(0.0f0,0.0f0,0.0f0,1.0f0)
```
