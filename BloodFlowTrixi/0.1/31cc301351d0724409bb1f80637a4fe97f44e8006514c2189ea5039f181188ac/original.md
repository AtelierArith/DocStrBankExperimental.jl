```
BloodFlowEquations1D(;h,rho=1.0,xi=0.25,nu=0.04)
```

Blood Flow equations in one space dimension. This model describes the dynamics of blood flow along a compliant artery using one-dimensional equations derived from the Navier-Stokes equations. The equations account for conservation of mass and momentum, incorporating the effect of arterial compliance and frictional losses.

The governing equations are given by

$$
\left\{\begin{aligned}
  \frac{\partial a}{\partial t} + \frac{\partial}{\partial x}(Q) &= 0 \\
  \frac{\partial Q}{\partial t} + \frac{\partial}{\partial x}\left(\frac{Q^2}{A} + A P(a)\right) &= P(a) \frac{\partial A}{\partial x} - 2 \pi R k \frac Q {A}\\
  P(a) &= P_{ext} + \frac{Eh\sqrt{\pi}}{1-\xi^2}\frac{\sqrt{A} - \sqrt{A_0}}{A_0} \\
  R &= \sqrt{\frac{A}{\pi}}
\end{aligned}\right.
$$
