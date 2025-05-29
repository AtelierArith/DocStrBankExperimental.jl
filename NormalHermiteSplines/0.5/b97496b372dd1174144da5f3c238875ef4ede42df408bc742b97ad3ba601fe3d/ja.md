`struct RK_H2{T <: AbstractFloat} <: ReproducingKernel_2`

ベッセルポテンシャル空間 $H^{n/2 + 5/2}_ε (R^n)$ の再生核のタイプを定義します（「二次マテーン核」）：

$$
V(\eta , \xi, \varepsilon) = \exp (-\varepsilon |\xi - \eta|)
             (3 + 3\varepsilon |\xi  - \eta| + \varepsilon ^2 |\xi - \eta| ^2 ) \, .
$$

# フィールド

  * `ε::T`: ベッセルポテンシャル空間の定義からの「スケーリングパラメータ」、構造体コンストラクタで省略可能ですが、そうでない場合はゼロより大きくなければなりません。
