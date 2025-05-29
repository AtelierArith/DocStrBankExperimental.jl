```
ShallowWaterTwoLayerEquations2D(gravity, H0, rho_upper, rho_lower)
```

二層浅水方程式 (2LSWE) は二次元空間で定義されます。方程式は次のようになります。

$$
\begin{alignat*}{8}
&\frac{\partial}{\partial t}h_{upper}
&&+ \frac{\partial}{\partial x}\left(h_{upper} v_{1,upper}\right)
&&+ \frac{\partial}{\partial y}\left(h_{upper} v_{2,upper}\right)  \quad
&&= \quad 0 \\
&\frac{\partial}{\partial t}\left(h_{upper} v_{1,upper}\right)
&&+ \frac{\partial}{\partial x}\left(h_{upper} v_{1,upper}^2 + \frac{gh_{upper}^2}{2}\right)
&&+ \frac{\partial}{\partial y}\left(h_{upper} v_{1,upper} v_{2,upper}\right) \quad
&&= -gh_{upper}\frac{\partial}{\partial x}\left(b+h_{lower}\right) \\
&\frac{\partial}{\partial t}\left(h_{upper} v_{2,upper}\right)
&&+ \frac{\partial}{\partial x}\left(h_{upper} v_{1,upper} v_{2,upper}\right)
&&+ \frac{\partial}{\partial y}\left(h_{upper} v_{2,upper}^2 + \frac{gh_{upper}^2}{2}\right)
&&= -gh_{upper}\frac{\partial}{\partial y}\left(b+h_{lower}\right)\\
&\frac{\partial}{\partial t}h_{lower}
&&+ \frac{\partial}{\partial x}\left(h_{lower} v_{1,lower}\right)
&&+ \frac{\partial}{\partial y}\left(h_{lower} v_{2,lower}\right)
&&= \quad 0 \\
&\frac{\partial}{\partial t}\left(h_{lower} v_{1,lower}\right)
&&+ \frac{\partial}{\partial x}\left(h_{lower} v_{1,lower}^2 + \frac{gh_{lower}^2}{2}\right)
&&+ \frac{\partial}{\partial y}\left(h_{lower} v_{1,lower} v_{2,lower}\right)
&&= -gh_{lower}\frac{\partial}{\partial x}\left(b+\frac{\rho_{upper}}{\rho_{lower}} h_{upper}\right)\\
&\frac{\partial}{\partial t}\left(h_{lower} v_{2,lower}\right)
&&+ \frac{\partial}{\partial x}\left(h_{lower} v_{1,lower} v_{2,lower}\right)
&&+ \frac{\partial}{\partial y}\left(h_{lower} v_{2,lower}^2 + \frac{gh_{lower}^2}{2}\right)
&&= -gh_{lower}\frac{\partial}{\partial y}\left(b+\frac{\rho_{upper}}{\rho_{lower}} h_{upper}\right)
\end{alignat*}
$$

2LSWEの未知数は、下層の水位 $h_{lower}$ と上層の水位 $h_{upper}$、およびそれぞれのx方向の速度 $v_{1,lower}$ と $v_{1,upper}$、y方向の速度 $v_{2,lower}$ と $v_{2,upper}$ です。重力加速度は `g` で示され、層の密度は $\rho_{upper}$ と $\rho_{lower}$ で示され、（おそらく）変動する底面地形関数は $b(x)$ で示されます。保守変数である水位 $h_{lower}$ は底面地形 $b$ から測定され、$h_{upper}$ は $h_{lower}$ に対して相対的に測定されるため、全水位を $H_{lower} = h_{lower} + b$ および $H_{upper} = h_{upper} + h_{lower} + b$ と定義します。

密度は $\rho_{upper} < \rho_{lower}$ となるように選択する必要があり、これにより重い流体 $\rho_{lower}$ が下層に、軽い流体 $\rho_{upper}$ が上層に配置されることが保証されます。

追加の量 $H_0$ は、初期条件を設定したり「静止湖」のバランスをテストするために便利な全水位の参照値を格納するために利用可能です。

底面地形関数 $b(x)$ は、特定の問題設定の初期条件ルーチン内で設定されます。

未知数に加えて、Trixi は現在、時間的に固定されているにもかかわらず、近似点での底面地形値を格納しています。これは、近似中に底面地形の勾配をその場で計算する便利さや、全水位 $H$ やエントロピー変数のような補助量を計算するために行われます。これにより、これらの方程式の実装や使用にさまざまな影響があります：

  * 底面地形に対応するフラックス値はゼロでなければなりません。
  * 初期条件、境界条件、またはソース項を定義する際に底面地形値を含める必要があります。
  * [`Trixi.AnalysisCallback`](@extref) がこの変数を分析します。
  * Trixi の視覚化ツールは、デフォルトで底面地形を視覚化します。

2LSWEの良い入門書は、次の書籍の第12章にあります：

  * Benoit Cushman-Roisin (2011) 地球物理流体力学への入門：物理的および数値的側面 [https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C](https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C) ISBN: 978-0-12-088759-0

```
