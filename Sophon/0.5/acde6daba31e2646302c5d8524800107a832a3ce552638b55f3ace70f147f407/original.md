```
Siren(in_dims::Int, out_dims::Int; hidden_dims::Int, num_layers::Int, omega=30.0f0,
      init_weight=nothing))
Siren(layer_sizes::Int...; omega=30.0f0, init_weight=nothing)
```

Sinusoidal Representation Network.

## Keyword Arguments

  * `omega`: The `ω₀` used for the first layer.
  * `init_weight`: The initialization algorithm for the weights of the **input** layer. Note that all hidden layers use `kaiming_uniform` as the initialization algorithm. The default is

    $$
        W\sim \mathcal{U}\left(-\frac{\omega}{fan_{in}}, \frac{\omega}{fan_{in}}\right)
    $$

## Examples

```julia
julia> Siren(2, 32, 32, 1; omega=5.0f0)
Chain(
    layer_1 = Dense(2 => 32, sin),      # 96 parameters
    layer_2 = Dense(32 => 32, sin),     # 1_056 parameters
    layer_3 = Dense(32 => 1),           # 33 parameters
)         # Total: 1_185 parameters,
          #        plus 0 states, summarysize 48 bytes.

julia> Siren(3, 1; hidden_dims=20, num_layers=3)
Chain(
    layer_1 = Dense(3 => 20, sin),      # 80 parameters
    layer_2 = Dense(20 => 20, sin),     # 420 parameters
    layer_3 = Dense(20 => 20, sin),     # 420 parameters
    layer_4 = Dense(20 => 1),           # 21 parameters
)         # Total: 941 parameters,
          #        plus 0 states, summarysize 64 bytes.

# Use your own initialization algorithm for the input layer.
julia> init_weight(rng::AbstractRNG, out_dims::Int, in_dims::Int) = randn(rng, Float32, out_dims, in_dims) .* 2.5f0
julia> chain = Siren(2, 1; num_layers = 4, hidden_dims = 50, init_weight = init_weight)
```

## Reference

[sitzmann2020implicit](@cite)
