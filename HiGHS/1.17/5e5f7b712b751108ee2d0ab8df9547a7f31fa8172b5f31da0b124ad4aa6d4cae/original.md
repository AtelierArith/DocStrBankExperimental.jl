```
Highs_getPrimalRay(highs, has_primal_ray, primal_ray_value)
```

Indicates whether a primal ray that is a certificate of primal unboundedness currently exists, and (at the expense of solving an LP) gets it if it does not and primal_ray_value is not nullptr.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `has_primal_ray`: A pointer to an int to store 1 if the primal ray exists.
  * `primal_ray_value`: An array of length [num_col] filled with the unbounded ray.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
