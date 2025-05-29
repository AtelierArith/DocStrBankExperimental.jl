```
LinearizedEulerEquations1D(v_mean_global, c_mean_global, rho_mean_global)
```

Linearized Euler equations in one space dimension. The equations are given by

$$
\partial_t
\begin{pmatrix}
    \rho' \\ v_1' \\ p'
\end{pmatrix}
+
\partial_x
\begin{pmatrix}
    \bar{\rho} v_1' + \bar{v_1} \rho ' \\ \bar{v_1} v_1' + \frac{p'}{\bar{\rho}} \\ \bar{v_1} p' + c^2 \bar{\rho} v_1'
\end{pmatrix}
=
\begin{pmatrix}
    0 \\ 0 \\ 0
\end{pmatrix}
$$

The bar $\bar{(\cdot)}$ indicates uniform mean flow variables and $c$ is the speed of sound. The unknowns are the perturbation quantities of the acoustic velocity $v_1'$, the pressure $p'$  and the density $\rho'$.
