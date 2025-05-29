```
sstdk(x::Array, m::Int)
```

m 番目のサンプル平均を使用して、時系列のサンプル標準偏差を計算します。

# 引数

  * `x::Array`: 時系列。
  * `m::Int`: サンプル平均の順序。

# 出力

  * `std::Real`: サンプル標準偏差。

# 例

```julia
julia> sstdk(randn(100), 20)
```
