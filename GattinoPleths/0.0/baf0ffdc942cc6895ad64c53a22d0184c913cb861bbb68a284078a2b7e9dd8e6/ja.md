```julia
download_resource(rm::RemoteChoroplethResource, uri::String = pwd()) -> ::ChoroplethResource
```

`RemoteChoroplethResource`をダウンロードし、新しくダウンロードされたファイルに対応する通常の`ChoroplethResource`を返します。この関数を呼び出すと、リソースは指定された`uri`にダウンロードされます。この関数が`choropleth`から呼び出されると、自動的にファイルが新しい`uri`に`pwd` * `RemoteChoroplethResource.name`でダウンロードされます。 –-

```example
const europe_map = RemoteChoroplethResource("europe", "https://raw.githubusercontent.com/ChifiSource/GattinoPleths-Resources/refs/heads/main/europe/europe_map.svg", 
680 => 520, Dict{String, Vector{Pair{String, String}}}())

local_euro_resource = download_resource(rm, "sample.svg")

choropleth = choropleth(x, y, local_euro_resource)

# `download_resource`ステップをスキップして、`RemoteChoroplethResource`の`name`の下に
#   ファイルを暗黙的にダウンロードすることもできます。

choropleth(x, y, europe_map)
```
