`interpolate(knots::Vector{T}, values::Vector{T},              d1_knots::Vector{T}, d1_values::Vector{T},              d2_knots::Vector{T}, d2_values::Vector{T},              kernel :: RK, factorize = true) where {T <: AbstractFloat, RK <: ReproducingKernel_3}`

関数の値とその一階および二階導関数の値を用いて、補間正規スプラインを作成します。

# 引数

  * `knots::Vector{T}`: 与えられた関数値の位置。
  * `values::Vector{T}`: `knots`における関数値。
  * `d1_knots::Vector{T}`: 与えられた関数導関数値の位置。
  * `d1_values::Vector{T}`: `d1_knots`における関数導関数の値。
  * `d2_knots::Vector{T}`: 与えられた関数二階導関数値の位置。
  * `d2_values::Vector{T}`: `d2_knots`における関数二階導関数の値。
  * `kernel::RK`: 正規スプラインが構築されるヒルベルト空間の再生核。               次の型の構造体オブジェクトでなければなりません:                 `RK_W3` または `RK_H3` - スプラインは二回微分可能な関数として構築されます。
  * `factorize::Bool`: グラム行列の因子分解を計算する必要があるかどうかを定義します。                 スプラインが初めて構築される場合は `true` に設定する必要があります。                 スプラインが最初に行ったのと同じノットで異なる関数値を用いて構築される場合は                 `false` に設定できます。

戻り値: なし。
