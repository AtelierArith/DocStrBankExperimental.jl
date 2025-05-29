```
XPRSgetcallbackpresolveredcosts(prob, djs, first, last)::available, djs
```

現在のコールバックに関連付けられた前処理された問題の解からの削減コストを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `djs::Union{XPRSallocatable,AbstractVector{Float64}}`: 削減コストが返される長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 削減コストを返す最初の列。
  * `last::Integer`: 削減コストを返す最後の列。

# 戻り値

  * `available::Int32`: この変数は、双対解が利用可能な場合に1に設定されます。
  * `djs::AbstractVector{Float64}`: 削減コストが返される長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetcallbackpresolveredcosts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbackpresolveredcosts.html) のドキュメントも参照してください。
