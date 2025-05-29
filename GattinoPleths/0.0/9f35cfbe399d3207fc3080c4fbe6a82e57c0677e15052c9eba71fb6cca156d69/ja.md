#### GattinoPleths - Gattinoのコロプレス視覚化

  * 2024年11月に[chifi](https://github.com/orgs/ChifiSource)によって作成されました。
  * このソフトウェアはMITライセンスです。

`GattinoPleths`は、`Gattino`視覚化ライブラリにシンプルなコロプレスインターフェースを追加します。

###### 目次

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
