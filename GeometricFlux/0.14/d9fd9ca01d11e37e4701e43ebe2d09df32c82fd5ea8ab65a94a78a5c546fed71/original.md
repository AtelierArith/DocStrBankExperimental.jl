```
ChebConv(in=>out, k; bias=true, init=glorot_uniform)
```

Chebyshev spectral graph convolutional layer.

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `k`: The order of Chebyshev polynomial.
  * `bias`: Add learnable bias.
  * `init`: Weights' initializer.

# Examples

```jldoctest
julia> cc = ChebConv(1024=>256, 5, relu)
ChebConv(1024 => 256, k=5, relu)
```

See also [`WithGraph`](@ref) for training layer with static graph.
