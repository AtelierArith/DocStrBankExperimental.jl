```
Highs_getDualUnboundednessDirection(highs, has_dual_unboundedness_direction, dual_unboundedness_direction_value)
```

Indicates whether a dual unboundedness direction (corresponding to a certificate of primal infeasibility) exists, and (at the expense of solving an LP) gets it if it does not and dual_unboundedness_direction is not nullptr

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `has_dual_unboundedness_direction`: A pointer to an int to store 1 if the dual unboundedness direction exists.
  * `dual_unboundedness_direction_value`: An array of length [num_col] filled with the unboundedness direction.
