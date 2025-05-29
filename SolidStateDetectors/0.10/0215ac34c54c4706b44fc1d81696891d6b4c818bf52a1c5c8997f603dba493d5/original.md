```
calculate_electric_field!(sim::Simulation{T}; n_points_in_φ::Union{Missing, Int} = missing)::Nothing
```

Calculates the [`ElectricField`](@ref) from the [`ElectricPotential`](@ref) stored in `sim.electric_potential` and stores it in `sim.electric_field`. 

## Arguments

  * `sim::Simulation{T}`: [`Simulation`](@ref) for which `sim.electric_potential` has already been calculated.

## Keywords

  * `n_points_in_φ::Union{Missing, Int}`: For a 2D [`ElectricPotential`](@ref) (cylindrical coordinates and symmetric in `φ`), `sim.electric_potential`   is extended to `n_points_in_φ` "layers" in `φ` in order to calculate a 3D [`ElectricField`]. If `n_points_in_φ` is `missing`, the    default value is `36`.

## Examples

```
calculate_electric_field!(sim, n_points_in_φ = 32)
```

!!! note
    This method only works if `sim.electric_potential` has already been calculated and is not `missing`.

