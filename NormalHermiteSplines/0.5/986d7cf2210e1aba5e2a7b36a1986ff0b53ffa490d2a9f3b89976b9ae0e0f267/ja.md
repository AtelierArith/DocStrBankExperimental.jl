`struct RK_H0{T <: AbstractFloat} <: ReproducingKernel_0`

ベッセルポテンシャル空間 $H^{n/2 + 1/2}_ε (R^n)$ の再生核のタイプを定義します（「基本マテールンカーネル」）：

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|) \, .
$$

# フィールド

  * `ε::T`: ベッセルポテンシャル空間の定義からの「スケーリングパラメータ」、構造体コンストラクタで省略可能ですが、そうでない場合はゼロより大きくなければなりません。
