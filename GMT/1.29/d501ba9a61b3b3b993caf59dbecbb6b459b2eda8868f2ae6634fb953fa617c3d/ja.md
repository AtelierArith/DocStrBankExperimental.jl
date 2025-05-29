```
readgeom(wkt::String; gdataset::Bool=false)
```

  * `wkt`: WKT文字列としてエンコードされたジオメトリを含む文字列
  * `gdataset`: `true`に設定すると、GMTタイプの代わりにGDALデータセットを返すよう強制します。

### 返り値

GMTデータセットまたはGDALデータセット

### 例

```julia
D = readgeom("POLYGON ((0 0, 0 10, 10 10, 10 0, 0 0))")
```
