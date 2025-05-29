```
PolytropicEulerEquations2D(gamma, kappa)
```

The polytropic Euler equations

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

for an ideal gas with ratio of specific heats `gamma` in two space dimensions. Here, $\rho$ is the density and $v_1$ and`v_2` the velocities and

$$
p = \kappa\rho^\gamma
$$

the pressure, which we replaced using this relation.
