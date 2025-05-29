```
XPRSgetrhs(prob, rhs, first, last)::rhs
```

指定された範囲の行に対する右辺要素を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rhs::Union{XPRSallocatable,AbstractVector{Float64}}`: 右辺要素を配置するための長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 範囲内の最初の行。
  * `last::Integer`: 範囲内の最後の行。

# 戻り値

  * `rhs::AbstractVector{Float64}`: 右辺要素を配置するための長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetrhs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrhs.html) のドキュメントも参照してください。
