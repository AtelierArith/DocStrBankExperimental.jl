```
ShallowWaterEquationsQuasi1D(; gravity_constant, H0 = 0)
```

The quasi-1D shallow water equations (SWE). The equations are given by

$$
\begin{aligned}
  \frac{\partial}{\partial t}(a h) + \frac{\partial}{\partial x}(a h v) &= 0 \\
    \frac{\partial}{\partial t}(a h v) + \frac{\partial}{\partial x}(a h v^2)
    + g a h \frac{\partial}{\partial x}(h + b) &= 0
\end{aligned}
$$

The unknown quantities of the Quasi-1D SWE are the water height $h$ and the scaled velocity $v$. The gravitational constant is denoted by `g`, the (possibly) variable bottom topography function $b(x)$, and (possibly) variable channel width $a(x)$. The water height $h$ is measured from the bottom topography $b$, therefore one also defines the total water height as $H = h + b$.

The additional quantity $H_0$ is also available to store a reference value for the total water height that is useful to set initial conditions or test the "lake-at-rest" well-balancedness.

The bottom topography function $b(x)$ and channel width $a(x)$ are set inside the initial condition routine for a particular problem setup. To test the conservative form of the SWE one can set the bottom topography variable `b` to zero and $a$ to one. 

In addition to the unknowns, Trixi.jl currently stores the bottom topography and channel width values at the approximation points  despite being fixed in time. This is done for convenience of computing the bottom topography gradients on the fly during the approximation as well as computing auxiliary quantities like the total water height $H$ or the entropy variables. This affects the implementation and use of these equations in various ways:

  * The flux values corresponding to the bottom topography and channel width must be zero.
  * The bottom topography and channel width values must be included when defining initial conditions, boundary conditions or source terms.
  * [`AnalysisCallback`](@ref) analyzes this variable.
  * Trixi.jl's visualization tools will visualize the bottom topography and channel width by default.
