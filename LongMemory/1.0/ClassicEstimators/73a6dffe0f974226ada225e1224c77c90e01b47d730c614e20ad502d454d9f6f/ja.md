```
autocorrelation_plot(x::Array, k::Int)
```

時系列の自己相関関数を計算します。

# 引数

  * `x::Array`: 時系列。
  * `k::Int`: 自己相関のラグ。

# 出力

  * `p1::Plots.Plot`: 自己相関関数。

# 例

```julia
julia> autocorrelation_plot(randn(100), 10)
```
