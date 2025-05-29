```
moment(X::Matrix}, m::Int, b::Int)
```

Returns: SymmetricTensor{Float, m}, a tensor of the m'th moment of X, where b is a block size. Calls 1 core or multicore moment function.
