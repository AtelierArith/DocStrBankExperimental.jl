```
CompressibleEulerEquations1D(gamma)
```

可圧性オイラー方程式

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho \\ \rho v_1 \\ \rho e
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
\rho v_1 \\ \rho v_1^2 + p \\ (\rho e +p) v_1
\end{pmatrix}
=
\begin{pmatrix}
0 \\ 0 \\ 0
\end{pmatrix}
$$

理想気体のための、比熱比 `gamma` を持つ1次元空間における方程式です。ここで、$\rho$ は密度、$v_1$ は速度、$e$ は特定の総エネルギー **ではなく** 特定の内部エネルギーであり、

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho v_1^2 \right)
$$

は圧力です。
