```julia
choropleth(x::Vector, y::Vector{<:Number}, resource::AbstractChoroplethResource, args ...) -> ::Gattino.Context
```

`choropleth` 関数は、地理的ラベル (x)、連続的な特徴 (y)、コロプレスリソースファイル (resource、`AbstractChoroplethResource`)、および提供された `Vector` の色からコロプレスを作成します。ローカル `ChoroplethResource` とリモート `RemoteChoroplethResource` の両方に対してディスパッチがあります。後者は、現在の作業ディレクトリにリソースの名前を付けたSVGファイルに新しいファイルをダウンロードします。作業ディレクトリに保存することはオプションですが、他の場所に保存するには、`download_resource` を使用してリモートリソースをローカルのものに「変換」します。

リソースは地域名の小文字の略語を使用します。

```julia
choropleth(x::Vector{String}, y::Vector{<:Number}, rs::ChoroplethResource, colors::Vector{String}) -> ::Context
choropleth(x::Vector{<:Any}, y::Vector{<:Number}, rs::RemoteChoroplethResource, args ...) -> ::Context
```

---

```example
countries = ["mx", "us", "ca", "uk", "br", "au", "it", "ch", "ru", "in", "cn", "gl", "af", "bd", "jp", "iq"]
pleth = choropleth(countries, [rand(1:100) for c in countries], GattinoPleths.world_map, red_and_blue)
```
