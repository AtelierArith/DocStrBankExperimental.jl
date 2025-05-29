```
KdVEquation1D(; gravity, D = 1.0, eta0 = 0.0)
```

KdV (Korteweg-de Vries) equation in one spatial dimension. The equation is given by

$$
\begin{aligned}
  \eta_t+\sqrt{g D} \eta_x+3 / 2 \sqrt{g / D} \eta \eta_x+1 / 6 \sqrt{g D} D^2 \eta_{x x x} &= 0.
\end{aligned}
$$

The unknown quantity of the KdV equation is the total water height $\eta$. The gravitational acceleration `gravity` is denoted by $g$ and the constant bottom topography (bathymetry) $b = \eta_0 - D$, where $\eta_0$ is the constant still-water surface and $D$ the still-water depth. The water height above the bathymetry is therefore given by $h = \eta - \eta_0 + D$. The KdV equation is only implemented for $\eta_0 = 0$.

The equations only support a flat bathymetry.

The KdV equation is first introduced by Joseph Valentin Boussinesq (1877) and rediscovered by Diederik Korteweg and Gustav de Vries in 1895.

The semidiscretization implemented here is a modification of the one proposed by Biswas, Ketcheson, Ranocha, and Schütz (2025) for the non-dimensionalized KdV equation $u_t + u u_x + u_{x x x} = 0.$

The semidiscretization looks the following:

$$
\begin{aligned}
  \eta_t+\sqrt{g D} D_1\eta+ 1 / 2 \sqrt{g / D} \eta D_1 \eta +  1 / 2 \sqrt{g / D} D_1 \eta^2 +1 / 6 \sqrt{g D} D^2 D_3\eta &= 0.
\end{aligned}
$$

where $D_1$ is a first-derivative operator, $D_3$ a third-derivative operator, and $D$ the still-water depth.

It conserves

  * the total water mass (integral of $\eta$) as a linear invariant

and if upwind operators ($D_3 = D_{1,+} D_1 D_{1,-}$) or wide-stencil operators ($D_3 = D_1^3$) are used for the third derivative, it also conserves

  * the energy (integral of $1/2\eta^2$)

for periodic boundary conditions.

  * Diederik Korteweg and Gustav de Vries (1895) On the change of form of long waves advancing in a rectangular canal, and on a new type of long stationary waves [DOI: 10.1080/14786449508620739](https://doi.org/10.1080/14786449508620739)
  * Abhijit Biswas, David I. Ketcheson, Hendrik Ranocha and Jochen Schütz (2025) Traveling-Wave Solutions and Structure-Preserving Numerical Methods for a Hyperbolic Approximation of the Korteweg-de Vries Equation [DOI: 10.1007/s10915-025-02898-x](https://doi.org/10.1007/s10915-025-02898-x)
