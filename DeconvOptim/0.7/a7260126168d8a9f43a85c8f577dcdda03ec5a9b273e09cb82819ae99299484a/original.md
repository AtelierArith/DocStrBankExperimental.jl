```
GR(; <keyword arguments>)
```

This function returns a function to calculate the Good's roughness regularizer of a n-dimensional array. 

# Arguments

  * `num_dims=2`: Dimension of the array that should be regularized
  * `sum_dims=[1, 2]`: A array containing the dimensions we want to sum over
  * `weights=nothing`: A array containing weights to weight the contribution of    different dimensions. If `weights=nothing` all dimensions are weighted equally.
  * `step=1`: A integer indicating the step width for the array indexing
  * `mode="forward"`: Either `"central"` or `"forward"` accounting for different   modes of the spatial gradient. Default is "forward".
  * `ϵ=1f-8` is a smoothness variable, to make it differentiable

# Examples

To create a regularizer for a 3D dataset where the third dimension has different contribution. For the derivative we use forward mode.

```julia-repl
julia> reg = GR(num_dims=2, sum_dims=[1, 2], weights=[1, 1], mode="forward");

julia> reg([1 2 3; 4 5 6; 7 8 9])
-26.36561871738898
```
