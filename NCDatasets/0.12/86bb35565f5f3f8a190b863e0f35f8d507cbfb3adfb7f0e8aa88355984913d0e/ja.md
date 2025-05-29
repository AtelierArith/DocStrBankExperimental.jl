```
cv = coord(v::Union{CFVariable,Variable},standard_name)
```

変数 `v` の座標を標準名 `standard_name` または [単位に基づく標準化されたヒューリスティックス](https://web.archive.org/web/20190918144052/http://cfconventions.org/cf-conventions/cf-conventions.html#latitude-coordinate) によって見つけます。ヒューリスティックスが座標を検出できない場合は、`standard_name` 属性を追加するために netCDF ファイルを修正することを検討してください。座標のすべての次元は、変数 `v` の次元でもなければなりません。

## 例

```julia
using NCDatasets
ds = NCDataset("file.nc")
ncv = ds["SST"]
lon = coord(ncv,"longitude")[:]
lat = coord(ncv,"latitude")[:]
v = ncv[:]
close(ds)
```
