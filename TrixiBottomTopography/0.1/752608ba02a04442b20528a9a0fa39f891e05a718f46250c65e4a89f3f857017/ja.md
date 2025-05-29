```
BilinearBSpline(x::Vector, y::Vector, z::Matrix)
```

この関数は、構造体 [`BilinearBSpline`](@ref) の入力を計算します。入力値は次のとおりです。

  * `x`: x方向に等間隔の値を含むベクトル
  * `y`: y方向に等間隔の値を含むベクトルで、y値間の間隔はx値間の間隔と同じでなければなりません
  * `z`: z方向の対応する値を含む行列。値は次のように順序付けられています：

$$
\begin{aligned}
   \begin{matrix}
        & & x_1 & x_2 & ... & x_n\\
        & & & & &\\
        y_1 & & z_{11} & z_{12} & ... & z_{1n}\\
        y_1 & & z_{21} & z_{22} & ... & z_{2n}\\
        \vdots & & \vdots & \vdots & \ddots & \vdots\\
        y_m & & z_{m1} & z_{m2} & ... & z_{mn}
   \end{matrix}
\end{aligned}
$$

バイリニアBスプライン補間は、`x`に少なくとも2つの値、`y`に少なくとも2つの値があり、ベクトル`x`と`y`の次元が行列`z`の次元に対応している場合にのみ可能です。

まず、データは [`sort_data`](@ref) によってソートされ、`x` と `y` の値が対応する行列 `z` とともに昇順であることが保証されます。

パッチサイズ `Delta` は、最初の `x` 値から2番目の `x` 値を引くことによって計算されます。これは、連続する `x` と `y` の値の間に等間隔しか考慮しないため可能です。パッチは、2つの連続する `x` と `y` の値の間の領域です。

バイリニアBスプライン補間では、制御点 `Q` は `z` 値に対応します。

バイリニアBスプラインの係数行列 `IP` は次のように固定されています。

$$
\begin{aligned}
  \begin{pmatrix}
    -1 & 1\\
    1 & 0
  \end{pmatrix}
\end{aligned}
$$

このスクリプトの計算に関する参考文献は、次の文献の第2章にあります。

  * Quentin Agrapart & Alain Batailly (2020), Cubic and bicubic spline interpolation in Python. [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)

```
