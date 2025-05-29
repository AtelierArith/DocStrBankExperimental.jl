```
XPRSgetqrowqmatrixtriplets(prob, row, rowqcol1, rowqcol2, rowqcoef)::ncoefs, rowqcol1, rowqcol2, rowqcoef
```

二次制約係数行列の非ゼロ要素を三重項（係数を持つインデックスペア）として返します。

最大の効率を達成するために、`XPRSgetqrowqmatrixtriplets`はこの行列の下三角部分のみを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 二次係数を返す行のインデックス。
  * `rowqcol1::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 三重項の最初のインデックス。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すことで、その情報を問い合わせないこともできます。
  * `rowqcol2::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 三重項の二番目のインデックス。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すことで、その情報を問い合わせないこともできます。
  * `rowqcoef::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 三重項の係数。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すことで、その情報を問い合わせないこともできます。

# 戻り値

  * `ncoefs::Int32`: 行の二次係数の数を返すために使用される引数。
  * `rowqcol1::Union{Nothing,AbstractVector{Int32}}`: 三重項の最初のインデックス。
  * `rowqcol2::Union{Nothing,AbstractVector{Int32}}`: 三重項の二番目のインデックス。
  * `rowqcoef::Union{Nothing,AbstractVector{Float64}}`: 三重項の係数。

C APIの対応する関数のドキュメント[XPRSgetqrowqmatrixtriplets](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqrowqmatrixtriplets.html)も参照してください。
