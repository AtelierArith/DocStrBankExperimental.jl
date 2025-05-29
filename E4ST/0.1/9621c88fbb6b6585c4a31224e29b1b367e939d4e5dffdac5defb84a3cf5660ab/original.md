```
get_pflow_branch(data, model, branch_idx, year_idx, hour_idx)
```

Return total power flow on a branch. 

  * If branch*idx*signed is positive then positive power flow is in the direction f*bus -> t*bus listed in the branch table. It is measuring the power flow out of f_bus.
  * If branch*idx*signed is negative then positive power flow is in the opposite direction, t*bus -> f*bus listed in the branch table. It is measuring the power flow out of t_bus.
  * To use this to retieve the variable values after the model has been optimized, wrap the function with value() like this: value.(get*pflow*branch).
