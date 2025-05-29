```
spline_interpolation(b_spline::BilinearBSpline, x::Number, y::Number)
```

入力は[`BilinearBSpline`](@ref)オブジェクトと、スプラインが評価される変数`x`と`y`です。

パラメータ`i`と`j`は、`(x,y)`が位置するパッチを示します。この情報は、`Q`から正しい制御点を取得するためにも使用されます。パッチは、2つの連続した`b_spline.x`および`b_spline.y`値の間の領域です。

`my`は、さらなる計算のために`x`を区間$[0,1]$にマッピングする中間変数です。`ny`は`y`に対して同様のことを行います。

`(x,y)`でスプラインを評価するには、以下を計算する必要があります：

$$
\begin{aligned}
c_{i,j,1}(\mu_i(x),\nu_j(y)) =
    \begin{bmatrix} \nu_j(y)\\ 1 \end{bmatrix}^T
    \underbrace{\begin{bmatrix} -1 & 1\\ 1 & 0 \end{bmatrix}}_{\text{IP}}
    \begin{bmatrix} Q_{i,j} & Q_{i,j+1}\\ Q_{i+1,j} & Q_{i+1,j+1} \end{bmatrix}
    \underbrace{\begin{bmatrix} -1 & 1\\ 1 & 0 \end{bmatrix}}_{\text{IP}^T}
    \begin{bmatrix} \mu_i(x) \\ 1\end{bmatrix}
\end{aligned}
$$

このスクリプトの計算に関する参考文献は、以下の第2章にあります。

  * Quentin Agrapart & Alain Batailly (2020) Cubic and bicubic spline interpolation in Python. [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)

```
