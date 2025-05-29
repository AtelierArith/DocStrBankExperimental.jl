```
ShallowWaterTwoLayerEquations1D(gravity, H0, rho_upper, rho_lower)
```

二層浅水方程式 (2LSWE) の一空間次元における方程式は次のように与えられます。

$$
\begin{alignat*}{4}
&\frac{\partial}{\partial t}h_{upper}
&&+ \frac{\partial}{\partial x}\left(h_{upper} v_{1,upper}\right)
&&= 0 \\
&\frac{\partial}{\partial t}\left(h_{upper}v_{1,upper}\right)
&&+ \frac{\partial}{\partial x}\left(h_{upper}v_{1,upper}^2 + \dfrac{gh_{upper}^2}{2}\right)
&&= -gh_{upper}\frac{\partial}{\partial x}\left(b+h_{lower}\right)\\
&\frac{\partial}{\partial t}h_{lower}
&&+ \frac{\partial}{\partial x}\left(h_{lower}v_{1,lower}\right)
&&= 0 \\
&\frac{\partial}{\partial t}\left(h_{lower}v_{1,lower}\right)
&&+ \frac{\partial}{\partial x}\left(h_{lower}v_{1,lower}^2 + \dfrac{gh_{lower}^2}{2}\right)
&&= -gh_{lower}\frac{\partial}{\partial x}\left(b+\dfrac{\rho_{upper}}{\rho_{lower}}h_{upper}\right).
\end{alignat*}
$$

2LSWE の未知数は、下層 $h_{lower}$ と上層 $h_{upper}$ の水位であり、それぞれの速度は $v_{1,upper}$ と $v_{1,lower}$ です。重力加速度は `g` で示され、層の密度は $\rho_{upper}$ と $\rho_{lower}$ で、（おそらく）変動する底面地形関数 $b(x)$ です。保存変数である水位 $h_{lower}$ は底面地形 $b$ から測定され、$h_{upper}$ は $h_{lower}$ に対して相対的に測定されるため、全水位を $H_{upper} = h_{upper} + h_{upper} + b$ および $H_{lower} = h_{lower} + b$ と定義します。

密度は $\rho_{upper} < \rho_{lower}$ となるように選ばれなければならず、これにより重い流体 $\rho_{lower}$ が下層に、軽い流体 $\rho_{upper}$ が上層に配置されることが保証されます。

追加の量 $H_0$ は、初期条件を設定したり「静止湖」のバランスをテストするのに役立つ全水位の参照値を格納するために利用可能です。

底面地形関数 $b(x)$ は、特定の問題設定の初期条件ルーチン内で設定されます。

未知数に加えて、Trixi は現在、時間的に固定されているにもかかわらず、近似点での底面地形値を格納しています。これは、近似中に底面地形の勾配を即座に計算する便利さや、全水位 $H$ やエントロピー変数のような補助量を計算するために行われています。これにより、これらの方程式の実装と使用にさまざまな影響があります：

  * 底面地形に対応するフラックス値はゼロでなければなりません。
  * 初期条件、境界条件、またはソース項を定義する際に底面地形値を含める必要があります。
  * [`Trixi.AnalysisCallback`](@extref) はこの変数を分析します。
  * Trixi の視覚化ツールは、デフォルトで底面地形を視覚化します。

2LSWE の良い入門書は、次の書籍の第12章にあります：

  * Benoit Cushman-Roisin (2011) 地球物理流体力学への入門：物理的および数値的側面 [https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C](https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C) ISBN: 978-0-12-088759-0

```
