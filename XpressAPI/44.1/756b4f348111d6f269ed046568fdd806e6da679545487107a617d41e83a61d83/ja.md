```
XPRSnlpcalcslacks(prob, solution, slack)::slack
```

与えられた解に対するスラック値を非線形問題で計算します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `solution::AbstractVector{Number}`: スラックが要求される解。
  * `slack::Union{XPRSallocatable,AbstractVector{Float64}}`: スラックを返すための長さNROWSのベクター。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。

# 戻り値

  * `slack::AbstractVector{Float64}`: スラックを返すための長さNROWSのベクター。

C APIの対応する関数のドキュメントも参照してください [XPRSnlpcalcslacks](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpcalcslacks.html)。
