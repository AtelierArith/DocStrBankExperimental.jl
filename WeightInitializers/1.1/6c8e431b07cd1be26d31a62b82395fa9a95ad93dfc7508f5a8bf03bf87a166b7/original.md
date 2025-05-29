```
sparse_init([::AbstractRNG=Utils.default_rng()], [T=Float32], dims::Integer...;
    sparsity::Number, std::Number=0.01) -> AbstractArray{T}
```

Creates a sparsely initialized weight matrix with a specified proportion of zeroed elements, using random numbers drawn from a normal distribution for the non-zero elements. This method was introduced in [1].

!!! note
    The sparsity parameter controls the proportion of the matrix that will be zeroed. For example, a sparsity of 0.3 means that approximately 30% of the elements will be set to zero. The non-zero elements are distributed according to a normal distribution, scaled by the std parameter.


# Arguments

  * `rng::AbstractRNG`: The random number generator to use.
  * `T::Type{<:Number}`: The numeric type of the elements in the returned array.
  * `dims::Integer...`: The dimensions of the weight matrix to be generated.
  * `sparsity::Number`: The proportion of elements to be zeroed. Must be between 0 and 1.
  * `std::Number=0.01`: The standard deviation of the normal distribution before applying `gain`.

# Returns

  * `AbstractArray{T}`: A sparsely initialized weight matrix of dimensions `dims` and type `T`.

# Examples

```jldoctest
julia> y = sparse_init(Xoshiro(123), Float32, 5, 5; sparsity=0.3, std=0.01);

julia> y isa Matrix{Float32}
true

julia> size(y) == (5, 5)
true
```

# References

[1] Martens, J, "Deep learning via Hessian-free optimization" Proceedings of the 27th International Conference on International Conference on Machine Learning. 2010.
