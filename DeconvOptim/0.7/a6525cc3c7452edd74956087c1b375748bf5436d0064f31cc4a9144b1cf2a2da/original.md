```
generate_spatial_grad_square(num_dims, sum_dims_arr, weights)
```

Generate the Tullio statement for calculating the squared spatial gradient over n dimensions. `num_dims` is the dimension of the array.  `sum_dims_arr` is a array indicating over which dimensions we must sum over. `weights` is a array of a weight for the different dimension. `ind1` and `ind2` are the offsets for the difference.
