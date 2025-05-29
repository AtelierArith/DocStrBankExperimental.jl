```
interpolate_series(X::Union{FloatMatrix, JMatrix{Float64}})
```

各系列を順番に補間し、欠損値を非欠損値のサンプル平均で置き換えます。

# 引数

  * `X`: 観測された測定値 (`nxT`)
