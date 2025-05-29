```
pcl_compress(indices::Array{Int64, 2})
```

Computes the Jacobian matrix for `compress`. Assume that `compress` does the following transformation:

```
indices, values (v) --> new_indices, new_values (u)
```

This function computes  $J_{ij} = \frac{\partial u_j}{\partial v_i}$
