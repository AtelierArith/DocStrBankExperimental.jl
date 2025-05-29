```
Tikhonov(; <keyword arguments>)
```

This function returns a function to calculate the Tikhonov regularizer of a n-dimensional array. 

# Arguments

  * `num_dims=2`:
  * `sum_dims=[1, 2]`: A array containing the dimensions we want to sum over
  * `weights=nothing`: A array containing weights to weight the contribution of    different dimensions. If `weights=nothing` all dimensions are weighted equally.
  * `step=1`: A integer indicating the step width for the array indexing
  * `mode="laplace"`: Either `"laplace"`, `"spatial_grad_square"`, `"identity"` accounting for different   modes of the Tikhonov regularizer. Default is `"laplace"`.

# Examples

To create a regularizer for a 3D dataset where the third dimension has different contribution.

```julia-repl
julia> reg = Tikhonov(num_dims=2, sum_dims=[1, 2], weights=[1, 1], mode="identity");

julia> reg([1 2 3; 4 5 6; 7 8 9])
285
```
