```
LinearBSpline(x::Vector, y::Vector)
```

この関数は、構造体 [`LinearBSpline`](@ref) の入力を計算します。入力値は次のとおりです。

  * `x`: x方向に等間隔の値を含むベクトル
  * `y`: y方向の値を含むベクトル

線形Bスプライン補間は、データセットに `x` の値が少なくとも2つ存在する場合にのみ可能です。

最初に、[`sort_data`](@ref) を介してデータがソートされ、`x` の値が昇順であることが保証されます。

パッチサイズ `Delta` は、2番目と1番目の `x` の値を引くことによって計算されます。これは、等間隔の `x` の値のみを考慮するため可能です。パッチは、2つの連続した `x` の値の間の領域です。

線形Bスプライン補間では、制御点 `Q` は `y` の値に対応します。

線形Bスプラインの係数行列 `IP` は次のように固定されています。

$$
\begin{aligned}
  \begin{pmatrix}
    -1 & 1\\
    1 & 0
  \end{pmatrix}
\end{aligned}
$$

このスクリプトの計算に関する参考文献は、次の書籍の第1章にあります。

  * Quentin Agrapart & Alain Batailly (2020),  Cubic and bicubic spline interpolation in Python.  [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
