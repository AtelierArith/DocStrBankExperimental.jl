```
copy_conflict(model::GenericModel)
```

Return a copy of the current conflict for the model `model` and a [`GenericReferenceMap`](@ref) that can be used to obtain the variable and constraint reference of the new model corresponding to a given `model`'s reference.

This is a convenience function that provides a filtering function for [`copy_model`](@ref).

## Note

Model copy is not supported in `DIRECT` mode, that is, when a model is constructed using the [`direct_model`](@ref) constructor instead of the [`Model`](@ref) constructor. Moreover, independently on whether an optimizer was provided at model construction, the new model will have no optimizer, that is, an optimizer will have to be provided to the new model in the [`optimize!`](@ref) call.

## Example

In the following example, a model `model` is constructed with a variable `x` and two constraints `c1` and `c2`. This model has no solution, as the two constraints are mutually exclusive. The solver is asked to compute a conflict with [`compute_conflict!`](@ref). The parts of `model` participating in the conflict are then copied into a model `iis_model`.

```julia
julia> using JuMP

julia> import Gurobi

julia> model = Model(Gurobi.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> @constraint(model, c1, x >= 2)
c1 : x ≥ 2

julia> @constraint(model, c2, x <= 1)
c2 : x ≤ 1

julia> optimize!(model)

julia> compute_conflict!(model)

julia> if get_attribute(model, MOI.ConflictStatus()) == MOI.CONFLICT_FOUND
           iis_model, reference_map = copy_conflict(model)
           print(iis_model)
       end
Feasibility
Subject to
 c1 : x ≥ 2
 c2 : x ≤ 1
```
