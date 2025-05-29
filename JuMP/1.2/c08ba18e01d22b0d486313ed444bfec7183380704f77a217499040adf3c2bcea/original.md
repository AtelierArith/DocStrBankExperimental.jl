```
shadow_price(con_ref::ConstraintRef)
```

Return the change in the objective from an infinitesimal relaxation of the constraint.

This value is computed from [`dual`](@ref) and can be queried only when `has_duals` is `true` and the objective sense is `MIN_SENSE` or `MAX_SENSE` (not `FEASIBILITY_SENSE`). For linear constraints, the shadow prices differ at most in sign from the `dual` value depending on the objective sense.

See also [`reduced_cost`](@ref JuMP.reduced_cost).

## Notes

  * The function simply translates signs from `dual` and does not validate the conditions needed to guarantee the sensitivity interpretation of the shadow price. The caller is responsible, e.g., for checking whether the solver converged to an optimal primal-dual pair or a proof of infeasibility.
  * The computation is based on the current objective sense of the model. If this has changed since the last solve, the results will be incorrect.
  * Relaxation of equality constraints (and hence the shadow price) is defined based on which sense of the equality constraint is active.
