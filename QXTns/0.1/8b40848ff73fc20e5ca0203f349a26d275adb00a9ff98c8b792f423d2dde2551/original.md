```
replace_with_svd!(tn::TensorNetwork,
                  tensor_id::Symbol,
                  left_indices::Array{<:Index, 1};
                  kwargs...)
```

Function to replace a tensor in a tensor network with its svd.

The indices contained in 'left_indices' are considered the row indices of the tensor when the svd is performed.

# Keywords

  * `maxdim::Int`: the maximum number of singular values to keep.
  * `mindim::Int`: the minimum number of singular values to keep.
  * `cutoff::Float64`: set the desired truncation error of the SVD.
