```
apply_initial_state!(sim::Simulation{T}, ::Type{ElectricPotential}, grid::Grid{T} = Grid(sim);
        not_only_paint_contacts::Bool = true, paint_contacts::Bool = true)::Nothing where {T <: SSDFloat}
```

Applies the initial state for the calculation of the [`ElectricPotential`](@ref). It overwrites `sim.electric_potential`, `sim.q_eff_imp`, `sim.q_eff_fix`, `sim.ϵ` and `sim.point_types` with the material properties and fixed potentials defined in `sim.detector`.

## Arguments

  * `sim::Simulation{T}`: [`Simulation`](@ref) for which the initial state should be applied.
  * `grid::Grid{T}`: [`Grid`](@ref) to apply the initial state on. If no `grid` is given,    a default `Grid` is determined from `sim`.

## Keywords

  * `not_only_paint_contacts::Bool = true`: Whether to only use the painting algorithm of the surfaces of [`Contact`](@ref)   without checking if points are actually inside them.   Setting it to `false` should improve the performance but the points inside of [`Contact`](@ref) are not fixed anymore.
  * `paint_contacts::Bool = true`: Enable or disable the painting of the surfaces of the [`Contact`](@ref) onto the `grid`.

## Examples

```julia
apply_initial_state!(sim, ElectricPotential, paint_contacts = false)
```
