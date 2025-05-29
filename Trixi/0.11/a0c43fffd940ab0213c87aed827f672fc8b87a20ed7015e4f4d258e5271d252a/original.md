```
CompressibleEulerMulticomponentEquations2D(; gammas, gas_constants)
```

Multicomponent version of the compressible Euler equations

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho v_1 \\ \rho v_2 \\ \rho e \\ \rho_1 \\ \rho_2 \\ \vdots \\ \rho_{n}
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
\rho v_1^2 + p \\ \rho v_1 v_2 \\ ( \rho e +p) v_1 \\ \rho_1 v_1 \\ \rho_2 v_1 \\ \vdots \\ \rho_{n} v_1
\end{pmatrix}
+
\frac{\partial}{\partial y}
\begin{pmatrix}
\rho v_1 v_2 \\ \rho v_2^2 + p \\ ( \rho e +p) v_2 \\ \rho_1 v_2 \\ \rho_2 v_2 \\ \vdots \\ \rho_{n} v_2
\end{pmatrix}
=
\begin{pmatrix}
0 \\ 0 \\ 0 \\ 0 \\ 0 \\ \vdots \\ 0
\end{pmatrix}
$$

for calorically perfect gas in two space dimensions. Here, $\rho_i$ is the density of component $i$, $\rho=\sum_{i=1}^n\rho_i$ the sum of the individual $\rho_i$, $v_1$, $v_2$ the velocities, $e$ the specific total energy **rather than** specific internal energy, and

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho (v_1^2 + v_2^2) \right)
$$

the pressure,

$$
\gamma=\frac{\sum_{i=1}^n\rho_i C_{v,i}\gamma_i}{\sum_{i=1}^n\rho_i C_{v,i}}
$$

total heat capacity ratio, $\gamma_i$ heat capacity ratio of component $i$,

$$
C_{v,i}=\frac{R}{\gamma_i-1}
$$

specific heat capacity at constant volume of component $i$.

In case of more than one component, the specific heat ratios `gammas` and the gas constants `gas_constants` in [kJ/(kg*K)] should be passed as tuples, e.g., `gammas=(1.4, 1.667)`.

The remaining variables like the specific heats at constant volume `cv` or the specific heats at constant pressure `cp` are then calculated considering a calorically perfect gas.
