```
DragCoefficientPressure2D(aoa, rho_inf, u_inf, l_inf)
```

Compute the drag coefficient

$$
C_{D,p} \coloneqq \frac{\oint_{\partial \Omega} p \boldsymbol n \cdot \psi_D \, \mathrm{d} S}
                        {0.5 \rho_{\infty} U_{\infty}^2 L_{\infty}}
$$

based on the pressure distribution along a boundary. In 2D, the freestream-tangent unit vector $\psi_D$ is given by

$$
\psi_D \coloneqq \begin{pmatrix} \cos(\alpha) \\ \sin(\alpha) \end{pmatrix}
$$

where $\alpha$ is the angle of attack.

Supposed to be used in conjunction with [`AnalysisSurfaceIntegral`](@ref) which stores the boundary information and semidiscretization.

  * `aoa::Real`: Angle of attack in radians (for airfoils etc.)
  * `rho_inf::Real`: Free-stream density
  * `u_inf::Real`: Free-stream velocity
  * `l_inf::Real`: Reference length of geometry (e.g. airfoil chord length)
