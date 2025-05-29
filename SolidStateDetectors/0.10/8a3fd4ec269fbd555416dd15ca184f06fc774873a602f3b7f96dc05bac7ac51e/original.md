```
simulate!( sim::Simulation{T}; kwargs...) where {T, S}
```

Performs a full chain simulation for a given [`Simulation`](@ref) by

1. calculating the [`ElectricPotential`](@ref),
2. calculating the [`ElectricField`](@ref),
3. calculating the [`WeightingPotential`](@ref) for each [`Contact`](@ref).

The output is stored in `sim.electric_potential`, `sim.electric_field` and `sim.weighting_potentials`, respectively.

There are several keyword arguments which can be used to tune the simulation.

## Arguments

  * `sim::Simulation{T}`: [`Simulation`](@ref) for which the full chain simulation should be performed.

## Keywords

  * `convergence_limit::Real`: `convergence_limit` times the bias voltage sets the convergence limit of the relaxation.   The convergence value is the absolute maximum difference of the potential between two iterations of all grid points.   Default of `convergence_limit` is `1e-7` (times bias voltage).
  * `refinement_limits`: Defines the maximum relative (to applied bias voltage) allowed differences    of the potential value of neighboured grid points    in each dimension for each refinement.

      * `rl::Real` -> One refinement with `rl` equal in all 3 dimensions.
      * `rl::Tuple{<:Real,<:Real,<:Real}` -> One refinement with `rl` set individual for each dimension.
      * `rl::Vector{<:Real}` -> `length(l)` refinements with `rl[i]` being the limit for the i-th refinement.
      * `rl::Vector{<:Real,<:Real,<:Real}}` -> `length(rl)` refinements with `rl[i]` being the limits for the `i`-th refinement.
  * `min_tick_distance::Tuple{<:Quantity, <:Quantity, <:Quantity}`: Tuple of the minimum allowed distance between    two grid ticks for each dimension. It prevents the refinement to make the grid too fine.   Default is `1e-5` for linear axes and `1e-5 / (0.25 * r_max)` for the polar axis in case of a cylindrical `grid`.
  * `max_tick_distance::Tuple{<:Quantity, <:Quantity, <:Quantity}`: Tuple of the maximum allowed distance between    two grid ticks for each dimension used in the initialization of the grid.   Default is 1/4 of size of the world of the respective dimension.
  * `max_distance_ratio::Real`: Maximum allowed ratio between the two distances in any dimension to the two neighbouring grid points.        If the ratio is too large, additional ticks are generated such that the new ratios are smaller than `max_distance_ratio`.       Default is `5`.
  * `depletion_handling::Bool`: Enables the handling of undepleted regions. Default is `false`.
  * `use_nthreads::Int`: Number of threads to use in the computation. Default is `Base.Threads.nthreads()`.   The environment variable `JULIA_NUM_THREADS` must be set appropriately before the Julia session was   started (e.g. `export JULIA_NUM_THREADS=8` in case of bash).
  * `sor_consts::Union{<:Real, NTuple{2, <:Real}}`: Two element tuple in case of cylindrical coordinates.   First element contains the SOR constant for `r` = 0.   Second contains the constant at the outer most grid point in `r`. A linear scaling is applied in between.   First element should be smaller than the second one and both should be `∈ [1.0, 2.0]`. Default is `[1.4, 1.85]`.   In case of Cartesian coordinates, only one value is taken.
  * `max_n_iterations::Int`: Set the maximum number of iterations which are performed after each grid refinement.   Default is `10000`. If set to `-1` there will be no limit.
  * `not_only_paint_contacts::Bool = true`: Whether to only use the painting algorithm of the surfaces of [`Contact`](@ref)   without checking if points are actually inside them.   Setting it to `false` should improve the performance but the points inside of [`Contact`](@ref) are not fixed anymore.
  * `paint_contacts::Bool = true`: Enable or disable the painting of the surfaces of the [`Contact`](@ref) onto the `grid`.
  * `verbose::Bool=true`: Boolean whether info output is produced or not.

See also [`calculate_electric_potential!`](@ref), [`calculate_electric_field!`](@ref) and [`calculate_weighting_potential!`](@ref).

## Example

```julia
simulate!(sim, refinement_limits = [0.3, 0.1, 0.05], max_distance_ratio = 4, max_n_iterations = 20000)
```
