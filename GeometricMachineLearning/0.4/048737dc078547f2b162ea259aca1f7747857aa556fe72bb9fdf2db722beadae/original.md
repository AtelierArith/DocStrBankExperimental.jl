```
Transformer(dim, n_heads, L)
```

Make an instance of the Transformer with `n_heads` for dimension `dim` and `L` blocks.

# Arguments

`Transformer` takes the following optional keyword arguments:

  * `activation = tanh`: the activation function used for the [`ResNetLayer`](@ref).
  * `Stiefel::Bool = false`: if the matrices $P^V$, $P^Q$ and $P^K$ should live on a manifold.
  * `add_connection::Bool = false`: if the input should by added to the ouput after the [`MultiHeadAttention`](@ref) layer.
  * `use_bias::Bool = true`: Specifies if the [`ResNetLayer`](@ref) should use a bias.
