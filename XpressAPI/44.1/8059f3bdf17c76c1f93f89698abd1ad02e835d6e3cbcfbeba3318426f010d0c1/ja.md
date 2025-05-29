```
XPRSgetsolution(prob, x, first, last)::status, x
```

XPRSoptimize、XPRSmipoptimize、XPRSlpoptimize、または `XPRSnlpoptimize` の最中または後に現行の解を取得するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::Union{XPRSallocatable,AbstractVector{Float64}}`: プライマル変数の値が返されるダブルポインタ。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 解の最初の列。
  * `last::Integer`: 解の最後の列。

# 戻り値

  * `status::Int32`: 返された解に関する情報。
  * `x::AbstractVector{Float64}`: プライマル変数の値が返されるダブルポインタ。

C APIの対応する関数 [XPRSgetsolution](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetsolution.html) のドキュメントも参照してください。
