```
naturalearth(name::String; version = v"5.1.2")
naturalearth(name::String, scale::Int; version = v"5.1.2")
```

`GeoJSON.FeatureCollection`オブジェクトとしてNaturalEarthデータセットをロードします。

`name`には`ne_`プレフィックスを含めず、`scale`を提供する場合もスケールを含めないでください。サフィックスは追加しないでください。

例えば、`ne_110m_admin_0_countries`データセットを取得するには、次のように使用できます：

```julia
naturalearth("admin_0_countries", 110)
naturalearth("110m_admin_0_countries")
```

https://github.com/nvkelso/natural-earth-vector/tree/master/geojsonにリストされているすべてのデータセットをサポートすることを目指しています。

!!! warning
    この関数は、ローカルに見つからない場合、インターネットからファイルをダウンロードします。

