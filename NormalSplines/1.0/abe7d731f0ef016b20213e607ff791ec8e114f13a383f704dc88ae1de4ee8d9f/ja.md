`struct RK_H2{T <: AbstractFloat} <: ReproducingKernel_2`

ベッセルポテンシャル空間 $H^2_ε (R)$ の再生カーネルの型を定義します：

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|)
             (1 + \varepsilon |\xi  - \eta|) \, .
$$

# 引数

  * 引数なし：パラメータ `ε` は補間手続きの実行中に推定されることを意味します。
  * `ε::T`：ベッセルポテンシャル空間の定義からの「スケーリングパラメータ」であり、ゼロより大きくなければなりません。
