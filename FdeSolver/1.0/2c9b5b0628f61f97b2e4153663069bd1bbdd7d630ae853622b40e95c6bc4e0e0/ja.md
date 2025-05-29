```
FDEsolver(F::Function, tSpan::Vector{<:Real}, y0::Union{Real, Vector{<:Real}, Matrix{<:Real}}, β::Union{Real, Vector{<:Real}}, par...; h = 2^-6, nc = 2, JF = nothing, tol = 1e-6, itmax = 100)
```

分数微分方程を予測修正アプローチで解きます。

# 引数

  * `F::Function`: 微分方程式系の右辺。関数の形で表現され、同じ数の導関数の順序を持つベクトル関数を返す必要があります。この関数にはパラメータのベクトル `par...` を含めることもできます。
  * `tSpan::Vector{<:Real}`: 計算が行われる時間範囲。
  * `y0::Union{Real, Vector{<:Real}, Matrix{<:Real}}`: 初期値は、$β <= 1$ の場合は行ベクトル（`Vector{<:Real}`）の形で、$β > 1$ の場合は行列（`Matrix{<:Real}`）の形で、各列が1つの微分方程式の初期値に対応し、各行が導出の順序に対応します。
  * `β::Union{Real, Vector{<:Real}}`: 行ベクトルの形での導出の順序で、各要素が1つの微分方程式の順序に対応します。小数および整数値を取ることができます。
  * `JF::Function`: Fのヤコビ行列。提供されない場合、ソルバーはヤコビ行列の助けを借りずに解を評価します。
  * `par...`: 関数Fのための追加パラメータ。
  * `h::Real`: 計算のステップサイズ。
  * `nc::Int64`: ヤコビ行列がない場合の予測修正法のための希望する修正回数。
  * `tol::Float64`: 誤差の許容範囲、各反復のノルムインフ（NR法の場合）またはnc>10のときの修正（PC法の場合）。
  * `ìtmax::Int64`: 最大反復回数。
