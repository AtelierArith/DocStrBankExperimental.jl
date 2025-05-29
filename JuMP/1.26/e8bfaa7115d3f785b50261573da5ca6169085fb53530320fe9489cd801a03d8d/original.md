```
shadow_price(con_ref::ConstraintRef)
```

Return the change in the objective from an infinitesimal relaxation of the constraint.

The shadow price is computed from [`dual`](@ref) and can be queried only when the [`objective_sense`](@ref) is [`MIN_SENSE`](@ref) or [`MAX_SENSE`](@ref) (not [`FEASIBILITY_SENSE`](@ref)).

See also [`reduced_cost`](@ref).

## Comparison to `dual`

The shadow prices differ at most in sign from the [`dual`](@ref) value depending on the [`objective_sense`](@ref). The differences are summarized in the table:

|             |      `MIN_SENSE` |      `MAX_SENSE` |
| -----------:| ----------------:| ----------------:|
| `f(x) <= b` |  `dual(con_ref)` | `-dual(con_ref)` |
| `f(x) >= b` | `-dual(con_ref)` |  `dual(con_ref)` |

## Notes

This function simply translates signs from [`dual`](@ref) and does not validate the conditions needed to guarantee the sensitivity interpretation of the shadow price. The caller is responsible, for example, for checking whether the solver converged to an optimal primal-dual pair or a proof of infeasibility.

The relaxation of equality constraints (and hence the shadow price) is defined based on which sense of the equality constraint is active.

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x);

julia> @constraint(model, c, x <= 1)
c : x ≤ 1

julia> @objective(model, Max, 2 * x + 1);

julia> optimize!(model)

julia> dual_status(model)
FEASIBLE_POINT::ResultStatusCode = 1

julia> shadow_price(c)
2.0

julia> dual(c)
-2.0
```
