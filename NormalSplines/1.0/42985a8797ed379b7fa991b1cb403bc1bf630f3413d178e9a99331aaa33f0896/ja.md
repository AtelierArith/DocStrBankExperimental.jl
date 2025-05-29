`interpolate(knots::Vector{T}, values::Vector{T},              d_knots::Vector{T}, d_values::Vector{T},              kernel :: RK, derivative = 1, factorize = true) where {T <: AbstractFloat, RK <: ReproducingKernel_2}`

ノーマルスプラインを、ノットにおける関数の値とその一次または二次導関数の値から作成します。

# 引数

  * `knots::Vector{T}`: 与えられた関数値の位置。
  * `values::Vector{T}`: `knots`における関数値。
  * `d_knots::Vector{T}`: 与えられた関数の一次導関数の値の位置（`derivative`=`1`の場合）                       または二次導関数の値の位置（`derivative`=`2`の場合）。
  * `d_values::Vector{T}`: `d_knots`における関数の一次導関数の値（`derivative`=`1`の場合）または                        関数の二次導関数の値（`derivative`=`2`の場合）。
  * `kernel::RK`: ノーマルスプラインが構築されるヒルベルト空間の再生核。               `derivative`=`1`の場合、`kernel`は次の型の構造体オブジェクトでなければなりません:                    `RK_W2`または`RK_H2`（スプラインが微分可能な関数として構築される場合）、                    `RK_W3`または`RK_H3`（スプラインが二回微分可能な関数として構築される場合）。               `derivative`=`2`の場合、`kernel`は次の型の構造体オブジェクトでなければなりません:                    `RK_W3`または`RK_H3` - スプラインは二回微分可能な関数として構築されます。
  * `derivative::Int`: `1` - `d_knots`と`d_values`は関数の一次導関数のデータを提供し、                    `2` - `d_knots`と`d_values`は関数の二次導関数のデータを提供します。
  * `factorize::Bool`: グラム行列の因子分解を計算する必要があるかどうかを定義します。                    スプラインが初めて構築される場合は`true`に設定する必要があります。                    同じノットで異なる関数値を用いてスプラインを構築する場合は`false`に設定できます。

返り値: なし。
