```
BloodFlowEquations2D(;h,rho=1.0,xi=0.25)
```

Defines the two-dimensional blood flow equations derived from the Navier-Stokes equations in curvilinear coordinates under the thin-artery assumption. This model describes the dynamics of blood flow along a compliant artery in two spatial dimensions (s, θ).

### Parameters

  * `h::T`: Wall thickness of the artery.
  * `rho::T`: Fluid density (default 1.0).
  * `xi::T`: Poisson's ratio (default 0.25).
  * `nu::T`: Viscosity coefficient.

The governing equations account for conservation of mass and momentum, incorporating the effects of arterial compliance, curvature, and frictional losses.

$$
\left\{\begin{aligned}
    \frac{\partial a}{\partial t} + \frac{\partial}{\partial \theta}\left( \frac{Q_{R\theta}}{A} \right) + \frac{\partial}{\partial s}(Q_s) &= 0 \\
    \frac{\partial Q_{R\theta}}{\partial t} + \frac{\partial}{\partial \theta}\left(\frac{Q_{R\theta}^2}{2A^2} + A P(a)\right) + \frac{\partial}{\partial s}\left( \frac{Q_{R\theta}Q_s}{A} \right) &= P(a) \frac{\partial A}{\partial \theta} - 2 R k \frac{Q_{R\theta}}{A} + \frac{2R}{3} \mathcal{C}\sin \theta \frac{Q_s^2}{A} \\
    \frac{\partial Q_{s}}{\partial t} + \frac{\partial}{\partial \theta}\left(\frac{Q_{R\theta} Q_s}{A^2} \right) + \frac{\partial}{\partial s}\left( \frac{Q_s^2}{A} - \frac{Q_{R\theta}^2}{2A^2} + A P(a) \right) &= P(a) \frac{\partial A}{\partial s} - R k \frac{Q_s}{A} - \frac{2R}{3} \mathcal{C}\sin \theta \frac{Q_s Q_{R\theta}}{A^2} \\
    P(a) &= P_{ext} + \frac{Eh}{\sqrt{2}\left(1-\xi^2\right)}\frac{\sqrt{A} - \sqrt{A_0}}{A_0} \\
    R &= \sqrt{2A}
\end{aligned}\right.
$$
