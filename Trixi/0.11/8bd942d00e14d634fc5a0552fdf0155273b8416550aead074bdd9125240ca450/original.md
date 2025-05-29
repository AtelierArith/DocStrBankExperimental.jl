```
MaxwellEquations1D(c = 299_792_458.0)
```

The Maxwell equations of electro dynamics

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
E \\ B
\end{pmatrix}
+ 
\frac{\partial}{\partial x}
\begin{pmatrix}
c^2 B \\ E
\end{pmatrix}
=
\begin{pmatrix}
0 \\ 0 
\end{pmatrix}
$$

in one dimension with speed of light `c = 299792458 m/s` (in vacuum). In one dimension the Maxwell equations reduce to a wave equation. The orthogonal magnetic (e.g.`B_y`) and electric field (`E_z`) propagate as waves  through the domain in `x`-direction. For reference, see 

  * e.g. p.15 of Numerical Methods for Conservation Laws: From Analysis to Algorithms  https://doi.org/10.1137/1.9781611975109
  * or equation (1) in https://inria.hal.science/hal-01720293/document
