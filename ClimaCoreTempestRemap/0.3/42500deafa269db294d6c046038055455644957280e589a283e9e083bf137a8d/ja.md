```
rll_mesh(filename::AbstractString; nlat=90, nlon = round(Int, nlat * 1.6); verbose=false)
```

正規緯度経度 (RLL) メッシュを作成し、Exodus 形式で `filename` に書き込みます。`nlat` は緯度セルの数で、`nlon` は経度セルの数です。

`verbose=true` に設定すると、情報が表示されます。

See [Tempest remap: mesh generation](https://github.com/ClimateGlobalChange/tempestremap/#mesh-generation)
