```
CompressibleEulerEquations1D(gamma)
```

The compressible Euler equations

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

for an ideal gas with ratio of specific heats `gamma` in one space dimension. Here, $\rho$ is the density, $v_1$ the velocity, $e$ the specific total energy **rather than** specific internal energy, and

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho v_1^2 \right)
$$

the pressure.
