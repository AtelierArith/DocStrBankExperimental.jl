```
apply_initial_state!(sim::Simulation{T}, ::Type{WeightingPotential}, contact_id::Int, grid::Grid{T} = Grid(sim))::Nothing
```

Applies the initial state for the calculation of the [`WeightingPotential`](@ref) for the [`Contact`}(@ref) with the id `contact_id`. It overwrites `sim.weighting_potentials[contact_id]` with the fixed values on the [`Contact`}(@ref).

## Arguments

  * `sim::Simulation{T}`: [`Simulation`](@ref) for which the initial state should be applied.
  * `contact_id::Int`: The `id` of the [`Contact`](@ref) for which the [`WeightingPotential`](@ref) is to be calculated.
  * `grid::Grid{T}`: [`Grid`](@ref) to apply the initial state on. If no `grid` is given,    a default `Grid` is determined from `sim`.

## Keywords

  * `not_only_paint_contacts::Bool = true`: Whether to only use the painting algorithm of the surfaces of [`Contact`](@ref)   without checking if points are actually inside them.   Setting it to `false` should improve the performance but the points inside of [`Contact`](@ref) are not fixed anymore.
  * `paint_contacts::Bool = true`: Enable or disable the painting of the surfaces of the [`Contact`](@ref) onto the `grid`.

## Examples

```julia
apply_initial_state!(sim, WeightingPotential, 1) # =>  applies initial state for weighting potential of contact with id 1
```
