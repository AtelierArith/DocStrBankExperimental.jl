```
ShallowWaterEquationsWetDry1D(; gravity, H0 = 0, threshold_limiter = nothing threshold_wet = nothing)
```

Shallow water equations (SWE) in one space dimension. The equations are given by

$$
\begin{aligned}
  \frac{\partial h}{\partial t} + \frac{\partial}{\partial x}(h v) &= 0 \\
    \frac{\partial}{\partial t}(h v) + \frac{\partial}{\partial x}\left(h v^2 + \frac{g}{2}h^2\right)
    + g h \frac{\partial b}{\partial x} &= 0
\end{aligned}
$$

The unknown quantities of the SWE are the water height $h$ and the velocity $v$. The gravitational acceleration is denoted by `g` and the (possibly) variable bottom topography function $b(x)$. Conservative variable water height $h$ is measured from the bottom topography $b$, therefore one also defines the total water height as $H = h + b$.

The additional quantity $H_0$ is also available to store a reference value for the total water height that is useful to set initial conditions or test the "lake-at-rest" well-balancedness.

Also, there are four thresholds which prevent numerical problems as well as instabilities. None of them have to be passed, as default values are defined within the struct. The first one, `threshold_limiter`, is used in [`PositivityPreservingLimiterShallowWater`](@ref) on the water height, as a (small) shift on the initial condition and cutoff before the next time step. The second one, `threshold_wet`, is applied on the water height to define when the flow is "wet" before calculating the numerical flux. A third  `threshold_partially_wet` is applied on the water height to define "partially wet" elements in  [`IndicatorHennemannGassnerShallowWater`](@ref), that are then calculated with a pure FV method to ensure well-balancedness. Lastly, `threshold_desingularization` is used in [`PositivityPreservingLimiterShallowWater`](@ref) for the velocity desingularization procedure. For `Float64` no threshold needs to be passed, as default values are  defined within the struct. For other number formats `threshold_partially_wet` must be provided.

The bottom topography function $b(x)$ is set inside the initial condition routine for a particular problem setup. To test the conservative form of the SWE one can set the bottom topography variable `b` to zero.

In addition to the unknowns, Trixi.jl currently stores the bottom topography values at the approximation points despite being fixed in time. This is done for convenience of computing the bottom topography gradients on the fly during the approximation as well as computing auxiliary quantities like the total water height $H$ or the entropy variables. This affects the implementation and use of these equations in various ways:

  * The flux values corresponding to the bottom topography must be zero.
  * The bottom topography values must be included when defining initial conditions, boundary conditions or source terms.
  * [`Trixi.AnalysisCallback`](@extref) analyzes this variable.
  * Trixi.jl's visualization tools will visualize the bottom topography by default.

References for the SWE are many but a good introduction is available in Chapter 13 of the book:

  * Randall J. LeVeque (2002) Finite Volume Methods for Hyperbolic Problems [DOI: 10.1017/CBO9780511791253](https://doi.org/10.1017/CBO9780511791253)
