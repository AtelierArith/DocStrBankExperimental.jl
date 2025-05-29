```
Highs_getRanging(highs, col_cost_up_value, col_cost_up_objective, col_cost_up_in_var, col_cost_up_ou_var, col_cost_dn_value, col_cost_dn_objective, col_cost_dn_in_var, col_cost_dn_ou_var, col_bound_up_value, col_bound_up_objective, col_bound_up_in_var, col_bound_up_ou_var, col_bound_dn_value, col_bound_dn_objective, col_bound_dn_in_var, col_bound_dn_ou_var, row_bound_up_value, row_bound_up_objective, row_bound_up_in_var, row_bound_up_ou_var, row_bound_dn_value, row_bound_dn_objective, row_bound_dn_in_var, row_bound_dn_ou_var)
```

Compute the ranging information for all costs and bounds. For nonbasic variables the ranging information is relative to the active bound. For basic variables the ranging information relates to...

For any values that are not required, pass NULL.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `col_cost_up_value`: The upper range of the cost value
  * `col_cost_up_objective`: The objective at the upper cost range
  * `col_cost_up_in_var`: The variable entering the basis at the upper cost range
  * `col_cost_up_ou_var`: The variable leaving the basis at the upper cost range
  * `col_cost_dn_value`: The lower range of the cost value
  * `col_cost_dn_objective`: The objective at the lower cost range
  * `col_cost_dn_in_var`: The variable entering the basis at the lower cost range
  * `col_cost_dn_ou_var`: The variable leaving the basis at the lower cost range
  * `col_bound_up_value`: The upper range of the column bound value
  * `col_bound_up_objective`: The objective at the upper column bound range
  * `col_bound_up_in_var`: The variable entering the basis at the upper column bound range
  * `col_bound_up_ou_var`: The variable leaving the basis at the upper column bound range
  * `col_bound_dn_value`: The lower range of the column bound value
  * `col_bound_dn_objective`: The objective at the lower column bound range
  * `col_bound_dn_in_var`: The variable entering the basis at the lower column bound range
  * `col_bound_dn_ou_var`: The variable leaving the basis at the lower column bound range
  * `row_bound_up_value`: The upper range of the row bound value
  * `row_bound_up_objective`: The objective at the upper row bound range
  * `row_bound_up_in_var`: The variable entering the basis at the upper row bound range
  * `row_bound_up_ou_var`: The variable leaving the basis at the upper row bound range
  * `row_bound_dn_value`: The lower range of the row bound value
  * `row_bound_dn_objective`: The objective at the lower row bound range
  * `row_bound_dn_in_var`: The variable entering the basis at the lower row bound range
  * `row_bound_dn_ou_var`: The variable leaving the basis at the lower row bound range

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
