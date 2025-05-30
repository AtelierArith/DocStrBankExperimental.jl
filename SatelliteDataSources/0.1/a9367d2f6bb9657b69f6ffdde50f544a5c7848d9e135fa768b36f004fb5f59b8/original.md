```
translate_color(::Type{AbstractSatellite}, layer::Symbol)
```

Translates a color such as `:red`, `:green`, or `:blue` to the corresponding band name.

# Example

```julia
julia> translate_color(Landsat8, :red)
:B4

julia> translate_color(Sentinel2{10}, :nir)
:B08

julia> translate_color(Sentinel2{20}, :nir)
:B8A
```
