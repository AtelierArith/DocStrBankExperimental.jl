```
compute_conflict!(model::GenericModel)
```

Compute a conflict if the model is infeasible.

The conflict is also called the Irreducible Infeasible Subsystem (IIS).

If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a [`NoOptimizer`](@ref) error is thrown.

The status of the conflict can be checked with the [`MOI.ConflictStatus`](@ref) model attribute. Then, the status for each constraint can be queried with the [`MOI.ConstraintConflictStatus`](@ref) attribute.

See also: [`copy_conflict`](@ref)

## Example

```julia
julia> using JuMP

julia> model = Model(Gurobi.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 0);

julia> @constraint(model, c1, x >= 2);

julia> @constraint(model, c2, x <= 1);

julia> optimize!(model)

julia> compute_conflict!(model)

julia> get_attribute(model, MOI.ConflictStatus())
CONFLICT_FOUND::ConflictStatusCode = 3
```
