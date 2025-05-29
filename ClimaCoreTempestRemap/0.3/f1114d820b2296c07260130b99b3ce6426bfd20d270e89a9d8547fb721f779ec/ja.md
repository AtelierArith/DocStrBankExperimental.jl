```
def_time_coord(nc::NCDataset, length=Inf, eltype=Float64;
    units = "seconds since 2020-01-01 00:00:00"
    kwargs...
)
```

NetCDFデータセット`nc`において、時間座標（次元 + 変数）`"time"`を定義します。デフォルトでは、その長さは無制限に設定されています。座標に対応する変数が返されます。

追加の属性はキーワード引数として追加できます。

# 例

```julia
timevar = add_time_coord!(nc; units = "seconds since 2020-01-01 00:00:00",)
timevar[:] = collect(0.0:0.5:60)
```
