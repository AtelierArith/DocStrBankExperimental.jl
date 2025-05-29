```
GeoMean(; dtype::Maybe{Type} = nothing, eps::StorageReal = 0.0)
```

幾何平均値を返す縮約操作です。

**パラメータ**

`dtype` - デフォルトの出力データ型は、入力データ型の[`float_dtype_for`](@ref)です。

`eps` - ゼロ値に対処するために、各値に追加され、生の幾何平均から減算される正則化因子です。
