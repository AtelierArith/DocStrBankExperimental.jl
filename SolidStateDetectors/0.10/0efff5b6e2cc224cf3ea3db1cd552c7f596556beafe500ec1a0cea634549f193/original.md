```
calculate_capacitance_matrix(sim::Simulation{T}; consider_multiplicity::Bool = true) where {T}
```

Calculates the Maxwell Capacitance `N×N`-Matrix in units of pF, where `N` is the number of contacts of `sim.detector`. The individual elements, $c_{i,j}$, are calculated via  [`calculate_mutual_capacitance(sim::Simulation, (i,j)::Tuple{Int,Int})`](@ref). The matrix should be symmetric. The difference of `C[i,j]` and `C[j,i]` are due  to numerical precision in the integration due to the different grids of the two weighting potentials.

## Arguments

  * `sim::Simulation`: [`Simulation`](@ref) for which the capacitance matrix is calculated.

## Keywords

  * `consider_multiplicity::Bool = true`: Whether symmetries of the system should be taken into account.    For example, in case of true coaxial detector center around the origin and calculated on a cartesian grid    with the `x-axis` going from `[0, x_max]` and the `y-axis` going from `[0, y_max]` the multiplicity is 4   and, if `consider_multiplicity == true`, the returned value is already multiplied by 4.
