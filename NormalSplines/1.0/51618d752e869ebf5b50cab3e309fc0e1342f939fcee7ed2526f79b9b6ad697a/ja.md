`struct RK_H3{T <: AbstractFloat} <: ReproducingKernel_3`

Bessel Potential空間$H^3_ε (R)$の再生核の型を定義します：

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|)
             (3 + 3\varepsilon |\xi  - \eta| + \varepsilon ^2 |\xi - \eta| ^2 ) \, .
$$

# 引数

  * 引数なし：パラメータ`ε`は補間手続きの実行中に推定されることを意味します。
  * `ε::T`：Bessel Potential空間の定義からの「スケーリングパラメータ」であり、ゼロより大きくなければなりません。
