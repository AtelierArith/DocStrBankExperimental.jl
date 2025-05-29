```
orthogonal([::AbstractRNG=Utils.default_rng()], [T=Float32], dims::Integer...;
    gain = 1)  -> AbstractArray{T, length(dims)}
```

Return an `AbstractArray{T}` of the given dimensions (`dims`) which is a (semi) orthogonal matrix, as described in [1].

The function constructs an orthogonal or semi-orthogonal matrix depending on the specified dimensions. For two dimensions, it returns a matrix where `dims = (rows, cols)`. For more than two dimensions, it computes an orthogonal matrix of size `prod(dims[1:(end - 1)])` by `dims[end]` before reshaping it to the original dimensions.

Cannot construct a vector, i.e., `length(dims) == 1` is forbidden.

# Arguments

  * `rng::AbstractRNG`: Random number generator.
  * `T::Type{<:Real}`: The type of the elements in the array.
  * `dims::Integer...`: The dimensions of the array.
  * `gain::Number`: Scaling factor for the elements of the orthogonal matrix.

# References

[1] Saxe, McClelland, Ganguli. "Exact solutions to the nonlinear dynamics of learning in deep linear neural networks", ICLR 2014, https://arxiv.org/abs/1312.6120
