```
NcVar(name::AbstractString,dimin::Union{NcDim,Array{NcDim,1}}
```

メモリ内に新しいNetCDF変数`name`を作成します。この変数は、`dimin`で指定されたNetCDF次元のリストに関連付けられています。

### キーワード引数

  * `atts` 変数の属性を表す辞書
  * `t` Juliaの型（`Int16`、`Int32`、`Float32`、`Float64`、`String`のいずれか）またはNetCDFデータ型（`NC_SHORT`、`NC_INT`、`NC_FLOAT`、`NC_DOUBLE`、`NC_CHAR`、`NC_STRING`）で、変数のデータ型を決定します。デフォルトは-1です
  * `compress` NetCDF4ファイルの変数の圧縮レベルを設定する整数。デフォルトは-1（圧縮なし）。圧縮レベルは1..9が有効です
