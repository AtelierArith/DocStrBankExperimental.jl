```
spline_interpolation(b_spline::LinearBSpline, x::Number)
```

入力は[`LinearBSpline`](@ref)オブジェクトと、スプラインが評価される変数`x`です。

パラメータ`i`は、変数`x`が位置するパッチを示します。このパラメータは、`Q`から正しい制御点を取得するためにも使用されます。パッチは、2つの連続した`b_spline.x`値の間の領域です。

`kappa`は、さらなる計算のために`x`を区間$[0,1]$にマッピングする中間変数です。

`x`でスプラインを評価するには、次の計算を行う必要があります。

$$
\begin{aligned}
c_{i,1}(\kappa_i(x)) =
    \begin{bmatrix}
        \kappa_i(x)\\ 1
    \end{bmatrix}^T
    \begin{bmatrix}
        -1 & 1\\1 & 0
    \end{bmatrix}
    \begin{bmatrix}
        Q_i\\Q_{i+1}
    \end{bmatrix}
\end{aligned}
$$

このスクリプトの計算に関する参考文献は、以下の第1章にあります。

  * Quentin Agrapart & Alain Batailly (2020), Cubic and bicubic spline interpolation in Python. [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
