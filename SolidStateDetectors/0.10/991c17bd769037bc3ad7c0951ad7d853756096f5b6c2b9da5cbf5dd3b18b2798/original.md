```
calculate_stored_energy(sim::Simulation; consider_multiplicity::Bool = true)
```

Calculates and returns the energy stored in the [`ElectricField`](@ref) of a  [`SolidStateDetector`](@ref) in a given [`Simulation`](@ref) in units of J.

## Arguments

  * `sim::Simulation{T}`: [`Simulation`](@ref) with `sim.detector` for which the stored energy is calculated.

## Keywords

  * `consider_multiplicity::Bool = true`: Whether symmetries of the system should be taken into account.    For example, in case of true coaxial detector center around the origin and calculated on a cartesian grid    with the `x-axis` going from `[0, x_max]` and the `y-axis` going from `[0, y_max]` the multiplicity is 4   and, if `consider_multiplicity == true`, the returned value is already multiplied by 4.
