```
varbyattrib(ds, attname = attval)
```

データセット `ds` において、属性 `attname` が値 `attval` に一致する変数のリストを返します。一致する変数がない場合、リストは空です。出力は `CFVariable` のリストです。

# 例

NetCDFファイル `results.nc` から標準名 "longitude" の最初の変数のすべてのデータを読み込みます。

```julia-repl
julia> ds = NCDataset("results.nc", "r");
julia> data = varbyattrib(ds, standard_name = "longitude")[1][:]
```
