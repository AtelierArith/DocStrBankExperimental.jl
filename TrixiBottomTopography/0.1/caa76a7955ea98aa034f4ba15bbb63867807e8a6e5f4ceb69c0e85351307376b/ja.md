```
spline_interpolation(b_spline::CubicBSpline, x::Number)
```

入力は[`CubicBSpline`](@ref)オブジェクトと、スプラインが評価される変数`x`です。

パラメータ`i`は、変数`x`が位置するパッチを示します。このパラメータは、`Q`から正しい制御点を取得するためにも使用されます。パッチは、2つの連続した`b_spline.x`値の間の領域です。

`kappa`は、さらなる計算のために$t$を区間$[0,1]$にマッピングする中間変数です。

`x`でスプラインを評価するには、次の計算を行う必要があります。

$$
\begin{aligned}
c_{i,3}\left(\kappa_i(x) \right) = \frac{1}{6}
    \begin{bmatrix}
        \kappa_i(x)^3\\ \kappa_i(x)^2\\ \kappa_i(x) \\1
    \end{bmatrix}^T
    \underbrace{\begin{bmatrix}
        -1 & 3 & -3 & 1\\
        3 & -6 & 3 & 0\\
        -3 & 0 & 3 & 0\\
        1 & 4 & 1 & 0
    \end{bmatrix}}_{\text{IP}}
    \begin{bmatrix}
        Q_{i,\text{free}}\\ Q_{i+1,\text{free}}\\ Q_{i+2,\text{free}}\\ Q_{i+3,\text{free}}
    \end{bmatrix}
\end{aligned}
$$

このスクリプトの計算に関する参考文献は、以下の第1章にあります。

  * Quentin Agrapart & Alain Batailly (2020), Cubic and bicubic spline interpolation in Python. [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
