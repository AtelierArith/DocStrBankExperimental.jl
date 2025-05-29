```
autocovariance(x::Array, k::Int)
```

時系列の自己共分散を計算します。

# 引数

  * `x::Array`: 時系列。
  * `k::Int`: 自己共分散のラグ。

# 出力

  * `acv::Array`: 自己共分散。

# 例

```julia
julia> autocovariance(randn(100), 2)
```
