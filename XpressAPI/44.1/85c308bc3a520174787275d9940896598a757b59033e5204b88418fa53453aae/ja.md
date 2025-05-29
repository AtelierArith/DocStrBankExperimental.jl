```
XPRSgetub(prob, ub, first, last)::ub
```

指定された範囲内の列の上限を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ub::Union{XPRSallocatable,AbstractVector{Float64}}`: 上限を配置するための長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 範囲内の最初の列。
  * `last::Integer`: 範囲内の最後の列。

# 戻り値

  * `ub::AbstractVector{Float64}`: 上限を配置するための長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetub](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetub.html) のドキュメントも参照してください。
