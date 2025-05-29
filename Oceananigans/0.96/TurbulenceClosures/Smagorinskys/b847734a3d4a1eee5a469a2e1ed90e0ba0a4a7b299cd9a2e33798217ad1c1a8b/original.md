```
DynamicCoefficient([FT=Float64;] averaging, schedule=IterationInterval(1), minimum_numerator=1e-32)
```

When used with `Smagorinsky`, it calculates the Smagorinsky coefficient dynamically from the flow according to the scale invariant procedure in [BouZeid05](@citet).

`DynamicCoefficient` requires an `averaging` procedure, which can be a `LagrangianAveraging` (which averages fluid parcels along their Lagrangian trajectory) or a tuple of integers indicating a directional averaging procedure along chosen dimensions (e.g. `averaging=(1,2)` uses averages in the `x` and `y` directions).

`DynamicCoefficient` is updated according to `schedule`, and `minimum_numerator` defines the minimum value that is acceptable in the denominator of the final calculation.

# Examples

```jldoctest
julia> using Oceananigans

julia> dynamic_coeff = DynamicCoefficient(averaging=(1, 2))
DynamicCoefficient with
├── averaging = (1, 2)
├── schedule = IterationInterval(1, 0)
└── minimum_numerator = 1.0e-32

julia> dynamic_smagorinsky = Smagorinsky(coefficient=dynamic_coeff)
Smagorinsky closure with
├── coefficient = DynamicCoefficient(averaging = (1, 2), schedule = IterationInterval(1, 0))
└── Pr = 1.0
```

The dynamic Smagorinsky above has its coefficient recalculated at every time step, which will almost certainly be very slow. To alleviate the high computational cost of the `DynamicCoefficient` calculation, users may introduce an approximation wherein the dynamic coefficient is recomputed only every so often. This is standard practice in the literature and, while in principle any frequency choice is possible (as long as the coefficient changes relatively slowly compared to a single time-step), all published studies seem to recalculate it every 5 steps (e.g., Bou-Zeid et al. 2005; Chen et al. 2016; Salesky et al. 2017; Chor et al 2021). This choice seems to stem from the results by Bou-Zeid et al. (2005) who found that considerably speed up simulations while still producing very similar results to an update frequency of every time step. Users can change the update frequency using the `schedule` keyword argument. For example, a `DynamicCoefficient` that gets updated every 4 timesteps is obtained via:

```jldoctest
julia> using Oceananigans

julia> dynamic_coeff = DynamicCoefficient(averaging=(1, 2), schedule=IterationInterval(4))
DynamicCoefficient with
├── averaging = (1, 2)
├── schedule = IterationInterval(4, 0)
└── minimum_numerator = 1.0e-32

julia> dynamic_smagorinsky = Smagorinsky(coefficient=dynamic_coeff)
Smagorinsky closure with
├── coefficient = DynamicCoefficient(averaging = (1, 2), schedule = IterationInterval(4, 0))
└── Pr = 1.0
```

# References

Bou-Zeid, Elie, Meneveau, Charles, and Parlange, Marc. (2005) A scale-dependent Lagrangian dynamic model for large eddy simulation of complex turbulent flows, Physics of Fluids, **17**, 025105.

Salesky, Scott T., Chamecki, Marcelo, and Bou-Zeid Elie. (2017) On the nature of the transition between roll and cellular organization in the convective boundary layer, Boundary-layer meteorology 163, 41-68.

Chen, Bicheng, Yang, Di, Meneveau, Charles and Chamecki, Marcelo. (2016) Effects of swell on transport and dispersion of oil plumes within the ocean mixed layer, Journal of Geophysical Research: Oceans, 121(5), pp.3564-3578.

Chor, Tomas, McWilliams, James C., Chamecki, Marcelo. (2021) Modifications to the K-Profile Parameterization with nondiffusive fluxes for Langmuir turbulence, Journal of Physical Oceanography, 51(5), pp.1503-1521.
