```
smean(x::Array)
```

時系列のサンプル平均を計算します。

# 引数

  * `x::Array`: 時系列。

# 出力

  * `mean::Real`: サンプル平均。

# 例

```julia
julia> smean(randn(100))
```
