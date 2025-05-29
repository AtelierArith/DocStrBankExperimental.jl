`struct RK_H1{T <: AbstractFloat} <: ReproducingKernel_1`

ベッセルポテンシャル空間 $H^{n/2 + 3/2}_ε (R^n)$ の再生核のタイプを定義します（「線形マテーンカーネル」）：

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|)
             (1 + \varepsilon |\xi  - \eta|) \, .
$$

# フィールド

  * `ε::T`: ベッセルポテンシャル空間の定義からの「スケーリングパラメータ」、構造体コンストラクタで省略可能ですが、そうでない場合はゼロより大きくなければなりません
