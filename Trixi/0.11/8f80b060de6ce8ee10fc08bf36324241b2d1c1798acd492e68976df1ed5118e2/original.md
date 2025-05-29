```
CompressibleEulerEquations3D(gamma)
```

The compressible Euler equations

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho \\ \rho v_1 \\ \rho v_2 \\ \rho v_3 \\  \rho e
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
 \rho v_1 \\ \rho v_1^2 + p \\ \rho v_1 v_2 \\ \rho v_1 v_3 \\ ( \rho e +p) v_1
\end{pmatrix}
+
\frac{\partial}{\partial y}
\begin{pmatrix}
\rho v_2 \\ \rho v_1 v_2 \\ \rho v_2^2 + p \\ \rho v_1 v_3 \\ ( \rho e +p) v_2
\end{pmatrix}
+
\frac{\partial}{\partial z}
\begin{pmatrix}
\rho v_3 \\ \rho v_1 v_3 \\ \rho v_2 v_3 \\ \rho v_3^2 + p \\ ( \rho e +p) v_3
\end{pmatrix}
=
\begin{pmatrix}
0 \\ 0 \\ 0 \\ 0 \\ 0
\end{pmatrix}
$$

for an ideal gas with ratio of specific heats `gamma` in three space dimensions. Here, $\rho$ is the density, $v_1$, $v_2$, $v_3$ the velocities, $e$ the specific total energy **rather than** specific internal energy, and

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho (v_1^2+v_2^2+v_3^2) \right)
$$

the pressure.
