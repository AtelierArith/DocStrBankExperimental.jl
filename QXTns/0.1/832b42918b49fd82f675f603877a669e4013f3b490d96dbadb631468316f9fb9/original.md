```
decompose_tensor!(tn::TensorNetwork,
                  tensor_id::Symbol,
                  left_indices::Array{<:Index, 1};
                  contract_S_with::Symbol=:V,
                  kwargs...)
```

Function to decompose a tensor in a tensor network using svd.

# Keywords

  * `contract_S_with::Symbol=:V`: the maxtrix which should absorb the matrix of singular values
  * `maxdim::Int`: the maximum number of singular values to keep.
  * `mindim::Int`: the minimum number of singular values to keep.
  * `cutoff::Float64`: set the desired truncation error of the SVD.
