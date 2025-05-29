```
XPRSgetcallbacksolution(prob, x, first, last)::available, x
```

現在のコールバックに関連付けられた解を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::Union{XPRSallocatable,AbstractVector{Float64}}`: プライマル変数の値が返される長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 返す解の最初の列。
  * `last::Integer`: 返す解の最後の列。

# 戻り値

  * `available::Int32`: 解が利用可能な場合、この変数は 1 に設定されます。
  * `x::AbstractVector{Float64}`: プライマル変数の値が返される長さ `last-first+1` のダブル配列。

C API の対応する関数 [XPRSgetcallbacksolution](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbacksolution.html) のドキュメントも参照してください。
