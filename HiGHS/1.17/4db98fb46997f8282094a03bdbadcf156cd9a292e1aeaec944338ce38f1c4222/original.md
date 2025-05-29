```
Highs_feasibilityRelaxation(highs, global_lower_penalty, global_upper_penalty, global_rhs_penalty, local_lower_penalty, local_upper_penalty, local_rhs_penalty)
```

Compute the solution corresponding to a (possibly weighted) sum of (allowable) infeasibilities in an LP/MIP.

If local penalties are not defined, pass NULL, and the global penalty will be used. Negative penalty values imply that the bound or RHS value cannot be violated

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `const`: double global_lower_penalty The penalty for violating lower bounds on variables
  * `const`: double global_upper_penalty The penalty for violating upper bounds on variables
  * `const`: double global_rhs_penalty The penalty for violating constraint RHS values
  * `const`: double* local_lower_penalty The penalties for violating specific lower bounds on variables
  * `const`: double* local_upper_penalty The penalties for violating specific upper bounds on variables
  * `const`: double* local_rhs_penalty The penalties for violating specific constraint RHS values

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
