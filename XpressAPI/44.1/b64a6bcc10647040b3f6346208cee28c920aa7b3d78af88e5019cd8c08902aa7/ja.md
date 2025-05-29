```
XPRSobjsa(prob, ncols, colind, lower, upper)::lower, upper
```

指定された目的関数係数の上限および下限感度範囲を返します。

目的係数がこれらの範囲内で変動する場合、現在の基準は最適のままであり、削減コストは有効のままです。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncols::Integer`: 感度を求める目的関数係数の数。
  * `colind::AbstractVector{Integer}`: 感度範囲が必要な目的関数係数の列のインデックスを含む長さ `ncols` の整数配列。
  * `lower::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 目的関数の下限範囲値が返される長さ `ncols` の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために、この引数に `nothing` を渡すこともできます。
  * `upper::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 目的関数の上限範囲値が返される長さ `ncols` の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために、この引数に `nothing` を渡すこともできます。

# 戻り値

  * `lower::Union{Nothing,AbstractVector{Float64}}`: 目的関数の下限範囲値が返される長さ `ncols` の倍精度配列。
  * `upper::Union{Nothing,AbstractVector{Float64}}`: 目的関数の上限範囲値が返される長さ `ncols` の倍精度配列。

C APIの対応する関数 [XPRSobjsa](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSobjsa.html) のドキュメントも参照してください。
