```
LinearizedEulerEquations2D(v_mean_global, c_mean_global, rho_mean_global)
```

2次元空間における線形化されたオイラー方程式。方程式は次のように与えられます。

$$
\partial_t
\begin{pmatrix}
    \rho' \\ v_1' \\ v_2' \\ p'
\end{pmatrix}
+
\partial_x
\begin{pmatrix}
    \bar{\rho} v_1' + \bar{v_1} \rho ' \\ \bar{v_1} v_1' + \frac{p'}{\bar{\rho}} \\ \bar{v_1} v_2' \\ \bar{v_1} p' + c^2 \bar{\rho} v_1'
\end{pmatrix}
+
\partial_y
\begin{pmatrix}
    \bar{\rho} v_2' + \bar{v_2} \rho ' \\ \bar{v_2} v_1' \\ \bar{v_2} v_2' + \frac{p'}{\bar{\rho}} \\ \bar{v_2} p' + c^2 \bar{\rho} v_2'
\end{pmatrix}
=
\begin{pmatrix}
    0 \\ 0 \\ 0 \\ 0
\end{pmatrix}
$$

バー記号 $\bar{(\cdot)}$ は一様平均流れの変数を示し、$c$ は音速です。未知数は音響速度 $v' = (v_1', v_2')$、圧力 $p'$、および密度 $\rho'$ です。
