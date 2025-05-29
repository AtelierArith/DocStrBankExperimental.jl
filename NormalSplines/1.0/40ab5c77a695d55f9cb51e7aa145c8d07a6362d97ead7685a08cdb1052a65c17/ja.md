`struct RK_H1{T <: AbstractFloat} <: ReproducingKernel_1`

ベッセルポテンシャル空間 $H^1_ε (R)$ の再生核の型を定義します：

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|) \, .
$$

# 引数

  * 引数なし：パラメータ `ε` は補間手続きの実行中に推定されることを意味します。
  * `ε::T`：ベッセルポテンシャル空間の定義からの「スケーリングパラメータ」で、ゼロより大きくなければなりません。
