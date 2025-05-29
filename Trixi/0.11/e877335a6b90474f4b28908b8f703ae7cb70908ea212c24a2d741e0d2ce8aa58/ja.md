```
ShallowWaterEquations2D(; gravity_constant, H0 = 0)
```

2次元の浅水方程式（SWE）。方程式は次のように与えられます。

$$
\begin{aligned}
  \frac{\partial h}{\partial t} + \frac{\partial}{\partial x}(h v_1)
    + \frac{\partial}{\partial y}(h v_2) &= 0 \\
    \frac{\partial}{\partial t}(h v_1) + \frac{\partial}{\partial x}\left(h v_1^2 + \frac{g}{2}h^2\right)
    + \frac{\partial}{\partial y}(h v_1 v_2) + g h \frac{\partial b}{\partial x} &= 0 \\
    \frac{\partial}{\partial t}(h v_2) + \frac{\partial}{\partial x}(h v_1 v_2)
    + \frac{\partial}{\partial y}\left(h v_2^2 + \frac{g}{2}h^2\right) + g h \frac{\partial b}{\partial y} &= 0.
\end{aligned}
$$

SWEの未知数は水の高さ $h$ と速度 $\mathbf{v} = (v_1, v_2)^T$ です。重力定数は `g` で表され、（おそらく）変動する底面地形関数 $b(x,y)$ です。保守変数である水の高さ $h$ は底面地形 $b$ から測定されるため、全水深を $H = h + b$ と定義します。

追加の量 $H_0$ は、初期条件を設定したり「静止湖」のバランスをテストするのに役立つ全水深の参照値を格納するために利用可能です。

底面地形関数 $b(x,y)$ は特定の問題設定の初期条件ルーチン内で設定されます。SWEの保守形式をテストするために、底面地形変数 `b` をゼロに設定することができます。

未知数に加えて、Trixi.jl は現在、時間的に固定されているにもかかわらず、近似点での底面地形値を格納しています。これは、近似中に底面地形の勾配を即座に計算する便利さや、全水深 $H$ やエントロピー変数のような補助量を計算するために行われています。これにより、これらの方程式の実装と使用にさまざまな影響があります：

  * 底面地形に対応するフラックス値はゼロでなければなりません。
  * 初期条件、境界条件、またはソース項を定義する際に底面地形値を含める必要があります。
  * [`AnalysisCallback`](@ref) はこの変数を分析します。
  * Trixi.jl の視覚化ツールはデフォルトで底面地形を視覚化します。

SWEに関する参考文献は多数ありますが、良い入門書は次の書籍の第13章にあります：

  * Randall J. LeVeque (2002) Finite Volume Methods for Hyperbolic Problems [DOI: 10.1017/CBO9780511791253](https://doi.org/10.1017/CBO9780511791253)
