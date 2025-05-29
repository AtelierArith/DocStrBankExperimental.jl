```
CompressibleEulerEquationsQuasi1D(gamma)
```

The quasi-1d compressible Euler equations (see Chan et al.  [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089)  for details)

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
a \rho \\ a \rho v_1 \\ a e
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
a \rho v_1 \\ a \rho v_1^2 \\ a v_1 (e +p)
\end{pmatrix}
+ 
a \frac{\partial}{\partial x}
\begin{pmatrix}
0 \\ p \\ 0    
\end{pmatrix}
=
\begin{pmatrix}
0 \\ 0 \\ 0
\end{pmatrix}
$$

for an ideal gas with ratio of specific heats `gamma` in one space dimension. Here, $\rho$ is the density, $v_1$ the velocity, $e$ the specific total energy **rather than** specific internal energy,  $a$ the (possibly) variable nozzle width, and

$$
p = (\gamma - 1) \left( e - \frac{1}{2} \rho v_1^2 \right)
$$

the pressure.

The nozzle width function $a(x)$ is set inside the initial condition routine for a particular problem setup. To test the conservative form of the compressible Euler equations one can set the  nozzle width variable $a$ to one. 

In addition to the unknowns, Trixi.jl currently stores the nozzle width values at the approximation points  despite being fixed in time. This affects the implementation and use of these equations in various ways:

  * The flux values corresponding to the nozzle width must be zero.
  * The nozzle width values must be included when defining initial conditions, boundary conditions or source terms.
  * [`AnalysisCallback`](@ref) analyzes this variable.
  * Trixi.jl's visualization tools will visualize the nozzle width by default.
