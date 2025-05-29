```
value_at_risk(R::TSFrame, p::Number=0.95; method::String="historical")
```

`Value-at-Risk(VaR)`を`資産リターン`から計算します。出力は`NamedArray`です。

# 引数:

  * `R::TSFrame`: 資産リターンのTSFrameオブジェクトの列
  * `p::Number=0.95`: 信頼水準
  * `method::String="historical"`: VaR計算の方法、利用可能な方法; `"historical"`および`"parametric"`

# 例

```julia
julia> var_historical = value_at_risk(returns)
4-element Named Vector{Float64}
95% historical VaR  │
────────────────────┼───────────
TSLA                │  -0.132252
NFLX                │ -0.0653681
MSFT                │  -0.035206

julia> var_parametric = value_at_risk(returns, 0.90, method = "parametric")
4-element Named Vector{Float64}
90% parametric VaR  │
────────────────────┼───────────
TSLA                │  -0.148553
NFLX                │ -0.0708139
MSFT                │ -0.0407369
```
