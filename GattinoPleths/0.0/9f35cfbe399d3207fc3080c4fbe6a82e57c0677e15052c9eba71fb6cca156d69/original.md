#### GattinoPleths - choropleth visualizations for Gattino

  * Created in November, 2024 by [chifi](https://github.com/orgs/ChifiSource)
  * This software is MIT-licensed.

`GattinoPleths` adds a simple choropleth interface to the `Gattino` visualization library.

###### contents

```julia
AbstractChoroplethResource
ChoroplethResource
RemoteChoroplethResource
download_resource(resource::RemoteChoroplethResource, uri::String = pwd())

world_map
europe_map
usa_map

choropleth_legend!(con::Gattino.AbstractContext, x::Pair{String, String}, colors::Vector{String}; align::String = "top-left")

choropleth(x::Vector{String}, y::Vector{<:Number}, rs::ChoroplethResource, colors::Vector{String} = ["red", "pink"])
choropleth(x::Vector{<:Any}, y::Vector{<:Number}, rs::RemoteChoroplethResource, args ...)
```
