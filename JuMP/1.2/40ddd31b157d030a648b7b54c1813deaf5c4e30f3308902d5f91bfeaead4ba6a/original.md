```
copy_conflict(model::Model)
```

Return a copy of the current conflict for the model `model` and a [`ReferenceMap`](@ref) that can be used to obtain the variable and constraint reference of the new model corresponding to a given `model`'s reference.

This is a convenience function that provides a filtering function for [`copy_model`](@ref).

## Note

Model copy is not supported in `DIRECT` mode, i.e. when a model is constructed using the [`direct_model`](@ref) constructor instead of the [`Model`](@ref) constructor. Moreover, independently on whether an optimizer was provided at model construction, the new model will have no optimizer, i.e., an optimizer will have to be provided to the new model in the [`optimize!`](@ref) call.

## Examples

In the following example, a model `model` is constructed with a variable `x` and two constraints `cref` and `cref2`. This model has no solution, as the two constraints are mutually exclusive. The solver is asked to compute a conflict with [`compute_conflict!`](@ref). The parts of `model` participating in the conflict are then copied into a model `new_model`.

```julia
model = Model() # You must use a solver that supports conflict refining/IIS
# computation, like CPLEX or Gurobi
@variable(model, x)
@constraint(model, cref, x >= 2)
@constraint(model, cref2, x <= 1)

compute_conflict!(model)
if MOI.get(model, MOI.ConflictStatus()) != MOI.CONFLICT_FOUND
    error("No conflict could be found for an infeasible model.")
end

new_model, reference_map = copy_conflict(model)
```
