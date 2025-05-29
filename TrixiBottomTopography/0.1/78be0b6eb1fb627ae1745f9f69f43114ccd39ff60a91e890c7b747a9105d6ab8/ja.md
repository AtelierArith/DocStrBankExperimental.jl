```
CubicBSpline(x::Vector, y::Vector; end_condition = "free", smoothing_factor = 0.0)
```

この関数は、構造 [`CubicBSpline`](@ref) の入力を計算します。入力値は次のとおりです。

  * `x`: x方向に等間隔の値を含むベクトル
  * `y`: y方向の値を含むベクトル
  * `end_condition`: `free` または `not-a-knot` のいずれかの文字列で、考慮すべき端条件を定義します。デフォルトでは "free" に設定されています。
  * `smoothing_factor`: Float64 $\geq$ 0.0 で、`y` 値の平滑化の度合いを指定します。デフォルトではこの値は `0.0` に設定されており、平滑化は行われません。

最初に、データは [`sort_data`](@ref) を介してソートされ、`x` 値が昇順になることが保証されます。

パッチサイズ `Delta` は、2番目と1番目の `x` 値を引き算することで計算されます。これは、等間隔の `x` 値のみを考慮するため可能です。（パッチは、2つの連続した `x` 値の間の領域です）

`smoothing_factor` が 0.0 より大きく設定されている場合、関数 [`spline_smoothing`](@ref) は、曲率が少ない B-スプラインを保証する新しい `y` 値を計算します。

線形 B-スプラインの係数行列 `IP` は次のように固定されています。

$$
\begin{aligned}
  IP = \begin{pmatrix}
    -1 & 3 & -3 & 1\\
    3 & -6 & 3 & 0\\
    -3 & 0 & 3 & 0\\
    1 & 4 & 1 & 0
  \end{pmatrix}
\end{aligned}
$$

"free" の端条件は、2番目と最後から2番目の制御点が最初と3番目の制御点の間にあり、最後から2番目の制御点が最後から3番目と最後の制御点の間にあることを要求します。この手順は、`x` データに少なくとも2つの値がある場合にのみ可能です。制御点を決定するための線形方程式の系は次の形を持ちます。

$$
\begin{aligned}
    \underbrace{\begin{bmatrix}
            0 \\ P_1 \\ P_2 \\ \vdots \\ P_{n-1} \\ P_n\\ 0
        \end{bmatrix}}_{:= P^*_{\text{free}}}
        = \frac{1}{6}
    \underbrace{
        \begin{bmatrix}
            1 & -2 & 1 & 0 & ... & ... & 0 \\
            1      & 4 & 1 & 0 & ... & ... & 0\\
            0      & 1 & 4 & 1 & 0   &     &     \vdots\\
            \vdots &  0      & \ddots & \ddots & \ddots & 0 & \vdots\\
            \vdots &       & 0 & 1 & 4 & 1 & 0\\
            0 & ... & ... & 0 & 1 & 4 & 1\\
            0 & ... & ... & 0 & 1 & -2 & 1
        \end{bmatrix}
    }_{:= \Phi^*_{\text{free}}}
    \underbrace{\begin{bmatrix}
        Q_1 \\ Q_2 \\ Q_3 \\ \vdots \\ Q_n \\ Q_{n+1} \\ Q_{n+2}
    \end{bmatrix}}_{:= Q_{\text{free}}},
\end{aligned}
$$

これは $Q_{\text{free}}$ を解くためのものです。

"not-a-knot" の端条件は、2番目と最後から2番目のフィットノットにおける3次導関数の連続性を要求します。この端条件は、`x` データに少なくとも4つの値がある場合にのみ可能です。制御点を決定するための線形方程式の系は次の形を持ちます。

$$
\begin{aligned}
    \underbrace{\begin{bmatrix}
        0 \\ P_1 \\ P_2 \\ \vdots \\ P_{n-1} \\ P_n\\ 0
    \end{bmatrix}}_{:= P^*_{\text{not-a-knot}}}
    = \frac{1}{6}
    \underbrace{
        \begin{bmatrix}
            -1 & 4 & -6 & 4 & -1 & 0 &... &  0 \\
            1      & 4 & 1 & 0 & ... & ... & ... & 0\\
            0      & 1 & 4 & 1 & 0   &     &     &\vdots\\
            \vdots &  0      & \ddots & \ddots & \ddots & 0 & &\vdots\\
            \vdots &  & 0      & \ddots & \ddots & \ddots & 0 &\vdots\\
            \vdots &    &   & 0 & 1 & 4 & 1 & 0\\
            0 & ... & ...  & ... & 0 & 1 & 4 & 1\\
            0 & ... & 0 & -1 & 4 & -6 & 4 & -1
        \end{bmatrix}
    }_{:= \Phi^*_{\text{not-a-knot}}}
    \underbrace{\begin{bmatrix}
        Q_1 \\ Q_2 \\ Q_3 \\ \vdots \\ \vdots \\ Q_n \\ Q_{n+1} \\ Q_{n+2}
    \end{bmatrix}}_{:= Q_{\text{not-a-knot}}}.
\end{aligned}
$$

これは $Q_{\text{not-a-knot}}$ を解くためのものです。

どちらの場合も $P_1,...,P_n = y_1,...,y_n$ です。

このスクリプトの計算に関する参考文献は、次の文献の第1章にあります。

  * Quentin Agrapart & Alain Batailly (2020),  Cubic and bicubic spline interpolation in Python.  [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)

```
