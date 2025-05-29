```
CompressibleNavierStokesDiffusion1D(equations; mu, Pr,
                                    gradient_variables=GradientVariablesPrimitive())
```

Contains the diffusion (i.e. parabolic) terms applied to mass, momenta, and total energy together with the advective terms from the [`CompressibleEulerEquations1D`](@ref).

  * `equations`: instance of the [`CompressibleEulerEquations1D`](@ref)
  * `mu`: dynamic viscosity,
  * `Pr`: Prandtl number,
  * `gradient_variables`: which variables the gradients are taken with respect to.                       Defaults to `GradientVariablesPrimitive()`.

Fluid properties such as the dynamic viscosity $\mu$ can be provided in any consistent unit system, e.g., [$\mu$] = kg m⁻¹ s⁻¹. The viscosity $\mu$ may be a constant or a function of the current state, e.g.,  depending on temperature (Sutherland's law): $\mu = \mu(T)$. In the latter case, the function `mu` needs to have the signature `mu(u, equations)`.

The particular form of the compressible Navier-Stokes implemented is

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho \\ \rho v \\ \rho e
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
 \rho v \\ \rho v^2 + p \\ (\rho e + p) v
\end{pmatrix}
=
\frac{\partial}{\partial x}
\begin{pmatrix}
0 \\ \tau \\ \tau v - q
\end{pmatrix}
$$

where the system is closed with the ideal gas assumption giving

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho v^2 \right)
$$

as the pressure. The value of the adiabatic constant `gamma` is taken from the [`CompressibleEulerEquations1D`](@ref). The terms on the right hand side of the system above are built from the viscous stress

$$
\tau = \mu \frac{\partial}{\partial x} v
$$

where the heat flux is

$$
q = -\kappa \frac{\partial}{\partial x} \left(T\right),\quad T = \frac{p}{R\rho}
$$

where $T$ is the temperature and $\kappa$ is the thermal conductivity for Fick's law. Under the assumption that the gas has a constant Prandtl number, the thermal conductivity is

$$
\kappa = \frac{\gamma \mu R}{(\gamma - 1)\textrm{Pr}}.
$$

From this combination of temperature $T$ and thermal conductivity $\kappa$ we see that the gas constant `R` cancels and the heat flux becomes

$$
q = -\kappa \frac{\partial}{\partial x} \left(T\right) = -\frac{\gamma \mu}{(\gamma - 1)\textrm{Pr}} \frac{\partial}{\partial x} \left(\frac{p}{\rho}\right)
$$

which is the form implemented below in the [`flux`](@ref) function.

In one spatial dimensions we require gradients for two quantities, e.g., primitive quantities

$$
\frac{\partial}{\partial x} v,\, \frac{\partial}{\partial x} T
$$

or the entropy variables

$$
\frac{\partial}{\partial x} w_2,\, \frac{\partial}{\partial x} w_3
$$

where

$$
w_2 = \frac{\rho v1}{p},\, w_3 = -\frac{\rho}{p}
$$
