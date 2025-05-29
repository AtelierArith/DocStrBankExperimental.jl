```
es(R::TSFrame, p::Number=0.95; method::String="historical")
```

`資産リターン`から`期待ショートフォール（条件付きバリューアットリスク）`を計算します。出力は`NamedArray`です。

# 引数:

  * `R::TSFrame`: 資産リターンのTSFrameオブジェクトの列
  * `p::Number=0.95`: 信頼水準
  * `method::String="historical"`: 期待ショートフォール計算の方法

# 例

```julia
julia> ES = es(returns)
4-element Named Vector{Any}
95% historical ES  │
───────────────────┼───────────
TSLA               │  -0.148766
NFLX               │ -0.0701279
MSFT               │  -0.066119
```

# 注意:

  * 利用可能な方法: `"historical"` と `"parametric"`
  * モンテカルロ法は次のリリースの一部として実装される予定です。
