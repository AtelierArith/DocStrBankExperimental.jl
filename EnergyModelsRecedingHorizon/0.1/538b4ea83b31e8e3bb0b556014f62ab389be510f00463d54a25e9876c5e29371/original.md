```
run_model_rh(case::AbstractCase, model::RecHorEnergyModel, optimizer; check_timeprofiles::Bool=true)
```

Take the variables `case` and `model` and optimize the problem in a receding horizon fashion as a series of optimization problems.

!!! warning "Required input"
    While the [`Case`](@extref EnergyModelsBase.Case) type is flexible, we have to follow certain structures.

      * The `case` type requires as additional input in the dictionary field `misc` the entry `:horizons` corresponding to an [`AbstractHorizons`](@ref) type.
      * The order of the individual elements vector in the field `elements` cannot be arbitrary at the moment due to the structure of the code. You **must** use the following order:

        1. `Vector{<:EMB.Node}`
        2. `Vector{<:Link}`
        3. `Vector{<:Area}`
        4. `Vector{<:Transmission}`

        If you do not use this structure, the model will not run.


Returns `results` as a dataframe indexed by the model variables.
