```
stddev(R::TSFrame)
```

`資産リターン`の`標準偏差`を計算します。出力は`NamedArray`です。

# 例

```julia
julia> stddev(returns)
4-element Named Vector{Float64}
σ    │
─────┼──────────
TSLA │  0.149608
NFLX │ 0.0637211
MSFT │ 0.0603753
```
