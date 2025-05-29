```
generate_TV(num_dims, sum_dims_arr, weights, ind1, ind2, ϵ)
```

Generate the Tullio statement for computing the Good's roughness. `num_dims` is the dimension of the array.  `sum_dims_arr` is a array indicating over which dimensions we must sum over. `weights` is a array of a weight for the different dimension. `ind1` and `ind2` are the offsets for the difference. `ϵ` is a numerical constant to prevent division by zero.      this is important for the gradient 
