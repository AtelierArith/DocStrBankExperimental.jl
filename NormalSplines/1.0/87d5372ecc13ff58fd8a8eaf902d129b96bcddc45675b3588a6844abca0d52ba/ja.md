`interpolate(knots::Vector{T}, values::Vector{T}, kernel :: RK, factorize = true) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

ノーマルスプラインをノットの関数値によって補間します。

# 引数

  * `knots::Vector{T}`: 与えられた関数値の位置。
  * `values::Vector{T}`: `knots`における関数値。
  * `kernel::RK`: ノーマルスプラインが構築されるヒルベルト空間の再生核。               構造体オブジェクトである必要があります。                 スプラインが連続関数として構築される場合は`RK_W1`または`RK_H1`、                 スプラインが微分可能な関数として構築される場合は`RK_W2`または`RK_H2`、                 スプラインが二回微分可能な関数として構築される場合は`RK_W3`または`RK_H3`。
  * `factorize::Bool`: グラム行列の因子分解を計算する必要があるかどうかを定義します。                 スプラインが初めて構築される場合は`true`に設定する必要があります。                 スプラインが最初に行ったのと同じノットで異なる関数値を持つ場合は                 `false`に設定できます。

戻り値: なし。
