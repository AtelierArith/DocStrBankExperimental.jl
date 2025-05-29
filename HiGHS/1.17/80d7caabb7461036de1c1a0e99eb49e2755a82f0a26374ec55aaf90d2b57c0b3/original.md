```
Highs_getDualRay(highs, has_dual_ray, dual_ray_value)
```

Indicates whether a dual ray that is a certificate of primal infeasibility currently exists, and (at the expense of solving an LP) gets it if it does not and dual_ray_value is not nullptr.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `has_dual_ray`: A pointer to an int to store 1 if a dual ray currently exists.
  * `dual_ray_value`: An array of length [num_row] filled with the unbounded ray.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
