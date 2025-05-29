```
PolytropicEulerEquations2D(gamma, kappa)
```

多体積Euler方程

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho \\ \rho v_1 \\ \rho v_2
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
 \rho v_1 \\ \rho v_1^2 + \kappa\rho^\gamma \\ \rho v_1 v_2
\end{pmatrix}
+
\frac{\partial}{\partial y}
\begin{pmatrix}
\rho v_2 \\ \rho v_1 v_2 \\ \rho v_2^2 + \kappa\rho^\gamma
\end{pmatrix}
=
\begin{pmatrix}
0 \\ 0 \\ 0
\end{pmatrix}
$$

理想気体のための、比熱比 `gamma` を持つ二次元空間における方程式です。ここで、$\rho$ は密度、$v_1$ と `v_2` は速度であり、

$$
p = \kappa\rho^\gamma
$$

この関係を用いて置き換えた圧力です。
