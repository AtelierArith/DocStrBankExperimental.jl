```
XPRSgetcallbackpresolvesolution(prob, x, first, last)::available, x
```

現在のコールバックに関連付けられた事前解決された問題の解を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::Union{XPRSallocatable,AbstractVector{Float64}}`: プライマル変数の値が返される長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 返す解の最初の列。
  * `last::Integer`: 返す解の最後の列。

# 戻り値

  * `available::Int32`: 解が利用可能な場合、この変数は1に設定されます。
  * `x::AbstractVector{Float64}`: プライマル変数の値が返される長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetcallbackpresolvesolution](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbackpresolvesolution.html) のドキュメントも参照してください。
