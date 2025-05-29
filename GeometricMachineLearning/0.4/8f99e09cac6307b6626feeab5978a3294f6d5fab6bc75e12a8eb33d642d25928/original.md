```
ClassificationTransformer(dl)
```

Make an instance of the `ClassificationTransformer` based on an instance of [`DataLoader`](@ref).

This is a transformer neural network for classification purposes. At the moment this is only used for training on MNIST, but can in theory be used for any classification problem.

# Arguments

The optional keyword arguments are: 

  * `n_heads::Int=7`: The number of heads in the `MultiHeadAttention` (mha) layers.
  * `L::Int=16`: The number of transformer blocks.
  * `activation=softmax`: The activation function.
  * `Stiefel::Bool=true`: Whether the matrices in the mha layers are on the [`StiefelManifold`](@ref).
  * `add_connection::Bool=true`: Whether the input is appended to the output of the mha layer. (skip connection)
