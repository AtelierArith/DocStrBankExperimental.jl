```
MultiHeadAttention(dim, n_heads)
```

Make a `MultiHeadAttention` layer with `n_heads` for a system of dimension `dim`. 

Note that the `dim` has to be divisible by `n_heads`.

MultiHeadAttention (MHA) serves as a preprocessing step in the transformer. 

It reweights the input vectors bases on correlations within those data.

This is used for the neural networks [`StandardTransformerIntegrator`](@ref) and [`ClassificationTransformer`](@ref).

# Arguments

The optional keyword arguments to `MultiHeadAttention` are:

  * `Stiefel::Bool=false`
  * `add_connection::Bool=true`
  * `activation::AbstractSoftmax=`[`VectorSoftmax`](@ref).

`Stiefel` indicates whether weights are put on the [`StiefelManifold`](@ref) $St(\mathrm{dim}, \mathrm{dim}\div\mathrm{n\_heads})$.

`add_connection` indicates whether the input is again added to the output.
