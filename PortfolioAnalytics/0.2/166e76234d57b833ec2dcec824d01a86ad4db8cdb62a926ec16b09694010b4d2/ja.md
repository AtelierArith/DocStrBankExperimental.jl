```
mean_return(R::TSFrame; geometric::Bool=true)
```

`資産リターン`から`平均リターン`を計算します。出力は`NamedArray`です。

# 引数:

  * `R::TSFrame`: 資産リターンのTSFrameオブジェクトの列
  * `geometric::Bool=true`: trueの場合、幾何平均を計算します

# 例

```julia
julia> mean_return(returns)
4-element Named Vector{Float64}
μ    │
─────┼───────────
TSLA │  0.0342267
NFLX │ 0.00904634
MSFT │  0.0350585


julia> mean_return(returns, geometric=false)
4-element Named Vector{Float64}
μ    │
─────┼──────────
TSLA │ 0.0431772
NFLX │  0.010848
MSFT │ 0.0366371
```
