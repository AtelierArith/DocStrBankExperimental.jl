```
CompressibleNavierStokesDiffusion3D(equations; mu, Pr,
                                    gradient_variables=GradientVariablesPrimitive())
```

Contains the diffusion (i.e. parabolic) terms applied to mass, momenta, and total energy together with the advective terms from the [`CompressibleEulerEquations3D`](@ref).

  * `equations`: instance of the [`CompressibleEulerEquations3D`](@ref)
  * `mu`: dynamic viscosity,
  * `Pr`: Prandtl number,
  * `gradient_variables`: which variables the gradients are taken with respect to.                       Defaults to `GradientVariablesPrimitive()`.

Fluid properties such as the dynamic viscosity $\mu$ can be provided in any consistent unit system, e.g., [$\mu$] = kg m⁻¹ s⁻¹. The viscosity $\mu$ may be a constant or a function of the current state, e.g.,  depending on temperature (Sutherland's law): $\mu = \mu(T)$. In the latter case, the function `mu` needs to have the signature `mu(u, equations)`.

The particular form of the compressible Navier-Stokes implemented is

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho \\ \rho \mathbf{v} \\ \rho e
\end{pmatrix}
+
\nabla \cdot
\begin{pmatrix}
 \rho \mathbf{v} \\ \rho \mathbf{v}\mathbf{v}^T + p \underline{I} \\ (\rho e + p) \mathbf{v}
\end{pmatrix}
=
\nabla \cdot
\begin{pmatrix}
0 \\ \underline{\tau} \\ \underline{\tau}\mathbf{v} - \mathbf{q}
\end{pmatrix}
$$

where the system is closed with the ideal gas assumption giving

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho (v_1^2+v_2^2+v_3^2) \right)
$$

as the pressure. The value of the adiabatic constant `gamma` is taken from the [`CompressibleEulerEquations2D`](@ref). The terms on the right hand side of the system above are built from the viscous stress tensor

$$
\underline{\tau} = \mu \left(\nabla\mathbf{v} + \left(\nabla\mathbf{v}\right)^T\right) - \frac{2}{3} \mu \left(\nabla\cdot\mathbf{v}\right)\underline{I}
$$

where $\underline{I}$ is the $3\times 3$ identity matrix and the heat flux is

$$
\mathbf{q} = -\kappa\nabla\left(T\right),\quad T = \frac{p}{R\rho}
$$

where $T$ is the temperature and $\kappa$ is the thermal conductivity for Fick's law. Under the assumption that the gas has a constant Prandtl number, the thermal conductivity is

$$
\kappa = \frac{\gamma \mu R}{(\gamma - 1)\textrm{Pr}}.
$$

From this combination of temperature $T$ and thermal conductivity $\kappa$ we see that the gas constant `R` cancels and the heat flux becomes

$$
\mathbf{q} = -\kappa\nabla\left(T\right) = -\frac{\gamma \mu}{(\gamma - 1)\textrm{Pr}}\nabla\left(\frac{p}{\rho}\right)
$$

which is the form implemented below in the [`flux`](@ref) function.

In two spatial dimensions we require gradients for three quantities, e.g., primitive quantities

$$
\nabla v_1,\, \nabla v_2,\, \nabla v_3,\, \nabla T
$$

or the entropy variables

$$
\nabla w_2,\, \nabla w_3,\, \nabla w_4\, \nabla w_5
$$

where

$$
w_2 = \frac{\rho v_1}{p},\, w_3 = \frac{\rho v_2}{p},\, w_4 = \frac{\rho v_3}{p},\, w_5 = -\frac{\rho}{p}
$$
