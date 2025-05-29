```
ShallowWaterMultiLayerEquations1D(gravity, H0, rhos)
```

Multi-Layer Shallow Water equations (MLSWE) in one space dimension. The equations are given by

$$
\left\{
	\begin{aligned}			
		&\partial_t h_m + \partial_x h_mv_m = 0,\\
		&\partial h_mv_m + \partial_x h_mv_m^2 = -gh_m\partial_x \bigg(b + \sum\limits_{k\geq j}h_k + \sum\limits_{k<m}\frac{\rho_k}{\rho_m}h_k \bigg)
	\end{aligned}
\right.
$$

where $m = 1, 2, ..., M$ is the layer index and the unknown variables are the water height $h$ and the velocity $v$.  Furthermore, $g$ denotes the gravitational acceleration, $b(x)$ the bottom  topography and $\rho_m$ the m-th layer density, that must be chosen such that  $\rho_1 < \rho_2 < ... < \rho_M$, to ensure that different layers are ordered from top to bottom, with  increasing density.

We use a specific formulation of the system, where the pressure term is reformulated as a  nonconservative term, which has some benefits for the design of well-balanced schemes.

The additional quantity $H_0$ is also available to store a reference value for the total water height that is useful to set initial conditions or test the "lake-at-rest" well-balancedness.

Also, there are two thresholds which prevent numerical problems as well as instabilities. The limiters are  used in [`PositivityPreservingLimiterShallowWater`](@ref) on the water height. `threshold_limiter`  acts as a (small) shift on the initial condition and cutoff before the next time step, whereas  `threshold_desingularization` is used in the velocity desingularization. A third  `threshold_partially_wet` is applied on the water height to define "partially wet" elements in  [`IndicatorHennemannGassnerShallowWater`](@ref), that are then calculated with a pure FV method to ensure well-balancedness. For `Float64` no threshold needs to be passed, as default values are  defined within the struct. For other number formats `threshold_desingularization` and `threshold_partially_wet`  must be provided.

The bottom topography function $b(x)$ is set inside the initial condition routine for a particular problem setup.

In addition to the unknowns, Trixi currently stores the bottom topography values at the approximation points despite being fixed in time. This is done for convenience of computing the bottom topography gradients on the fly during the approximation as well as computing auxiliary quantities like the total water height $H$ or the entropy variables. This affects the implementation and use of these equations in various ways:

  * The flux values corresponding to the bottom topography must be zero.
  * The bottom topography values must be included when defining initial conditions, boundary conditions or source terms.
  * [`Trixi.AnalysisCallback`](@extref) analyzes this variable.
  * Trixi's visualization tools will visualize the bottom topography by default.

A good introduction for the MLSWE is available in Chapter 12 of the book:     - Benoit Cushman-Roisin (2011)
      Introduction to geophyiscal fluid dynamics: physical and numerical aspects
      [https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C](https://www.sciencedirect.com/bookseries/international-geophysics/vol/101/suppl/C)
      ISBN: 978-0-12-088759-0
