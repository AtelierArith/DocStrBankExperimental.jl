```julia
choropleth(x::Vector, y::Vector{<:Number}, resource::AbstractChoroplethResource, args ...) -> ::Gattino.Context
```

The `choropleth` function will create a choropleth from geographic labels (x), a continuous feature (y), a choropleth resource file (resource, an `AbstractChoroplethResource`), and  a provided `Vector` of colors. There is a dispatch for both a local `ChoroplethResource` and the  remote `RemoteChoroplethResource`. The latter will download a new file into an SVG file named  after the resource in your current working directory. Storing in your working directory is optional,  but in order to store elsewhere, use `download_resource` to " convert" a remote resource into a local one.

The resources will use lower-case abbreviations for region names.

```julia
choropleth(x::Vector{String}, y::Vector{<:Number}, rs::ChoroplethResource, colors::Vector{String}) -> ::Context
choropleth(x::Vector{<:Any}, y::Vector{<:Number}, rs::RemoteChoroplethResource, args ...) -> ::Context
```

---

```example
countries = ["mx", "us", "ca", "uk", "br", "au", "it", "ch", "ru", "in", "cn", "gl", "af", "bd", "jp", "iq"]
pleth = choropleth(countries, [rand(1:100) for c in countries], GattinoPleths.world_map, red_and_blue)
```
