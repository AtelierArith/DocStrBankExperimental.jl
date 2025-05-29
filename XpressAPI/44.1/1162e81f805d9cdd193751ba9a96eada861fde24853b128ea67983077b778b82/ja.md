```
XPRSgetcallbackpresolveslacks(prob, slacks, first, last)::available, slacks
```

現在のコールバックに関連付けられた事前解決された問題の解からスラック値を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `slacks::Union{XPRSallocatable,AbstractVector{Float64}}`: スラック変数の値が返される長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: スラック値を返す最初の行。
  * `last::Integer`: スラック値を返す最後の行。

# 戻り値

  * `available::Int32`: 解が利用可能な場合、この変数は1に設定されます。
  * `slacks::AbstractVector{Float64}`: スラック変数の値が返される長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetcallbackpresolveslacks](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbackpresolveslacks.html) のドキュメントも参照してください。
