```
FourierNet(ayer_sizes::NTuple, activation, modes::NTuple)
```

A model that combines [`FourierFeature`](@ref) and [`FullyConnected`](@ref).

```
x → FourierFeature → FullyConnected → y
```

# Arguments

  * `in_dims`: The number of input dimensions.
  * `layer_sizes`: A tuple of hidden dimensions used to construct `FullyConnected`.
  * `activation`: The activation function used to construct `FullyConnected`.
  * `modes`: A tuple of modes used to construct `FourierFeature`.

# Examples

```julia
julia> FourierNet((2, 30, 30, 1), sin, (1 => 10, 10 => 10, 50 => 10))
Chain(
    layer_1 = FourierFeature(2 => 60),
    layer_2 = Dense(60 => 30, sin),     # 1_830 parameters
    layer_3 = Dense(30 => 30, sin),     # 930 parameters
    layer_4 = Dense(30 => 1),           # 31 parameters
)         # Total: 2_791 parameters,
          #        plus 60 states, summarysize 112 bytes.

julia> FourierNet((2, 30, 30, 1), sin, (1, 2, 3, 4))
Chain(
    layer_1 = FourierFeature(2 => 16),
    layer_2 = Dense(16 => 30, sin),     # 510 parameters
    layer_3 = Dense(30 => 30, sin),     # 930 parameters
    layer_4 = Dense(30 => 1),           # 31 parameters
)         # Total: 1_471 parameters,
          #        plus 4 states, summarysize 96 bytes.
```
