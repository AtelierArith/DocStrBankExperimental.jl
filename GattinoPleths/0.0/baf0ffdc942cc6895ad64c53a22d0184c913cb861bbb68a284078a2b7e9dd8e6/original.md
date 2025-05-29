```julia
download_resource(rm::RemoteChoroplethResource, uri::String = pwd()) -> ::ChoroplethResource
```

Downloads a `RemoteChoroplethResource`, providing a normal `ChoroplethResource` corresponding  to the newly downloaded file in return. When calling this function, the resource will download  to the provided `uri`. When this function is called from `choropleth`, it will automatically download  the file into a new `uri` at `pwd` * `RemoteChoroplethResource.name`. –-

```example
const europe_map = RemoteChoroplethResource("europe", "https://raw.githubusercontent.com/ChifiSource/GattinoPleths-Resources/refs/heads/main/europe/europe_map.svg", 
680 => 520, Dict{String, Vector{Pair{String, String}}}())

local_euro_resource = download_resource(rm, "sample.svg")

choropleth = choropleth(x, y, local_euro_resource)

# we can also skip the `download_resource` step to implicitly download the file 
#   under the `RemoteChoroplethResource`'s `name`.

choropleth(x, y, europe_map)
```
