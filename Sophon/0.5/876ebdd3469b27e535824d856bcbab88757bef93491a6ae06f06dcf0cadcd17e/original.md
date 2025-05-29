```
FourierAttention(in_dims::Int, out_dims::Int, activation::Function, std;
                 hidden_dims::Int=512, num_layers::Int=6, modes::NTuple)
FourierAttention(in_dims::Int, out_dims::Int, activation::Function, frequencies;
                 hidden_dims::Int=512, num_layers::Int=6, modes::NTuple)
```

A model that combines [`FourierFeature`](@ref) and [`PINNAttention`](@ref).

```
x → [FourierFeature(x); x] → PINNAttention
```

## Arguments

  * `in_dims`: The input dimension.

      * `out_dims`: The output dimension.
      * `activation`: The activation function.
      * `std`: See [`FourierFeature`](@ref).
      * `frequencies`: See [`FourierFeature`](@ref).

## Keyword Arguments

  * `hidden_dim`: The hidden dimension of each hidden layer.
  * `num_layers`: The number of hidden layers.

## Examples

```julia
julia> FourierAttention(3, 1, sin, (1 => 10, 10 => 10, 50 => 10); hidden_dims=10, num_layers=3)
Chain(
    layer_1 = SkipConnection(
        FourierFeature(3 => 60),
        vcat
    ),
    layer_2 = PINNAttention(
        H_net = Dense(63 => 10, sin),   # 640 parameters
        U_net = Dense(63 => 10, sin),   # 640 parameters
        V_net = Dense(63 => 10, sin),   # 640 parameters
        fusion = TriplewiseFusion(
            layers = (layer_1 = Dense(10 => 10, sin), layer_2 = Dense(10 => 10, sin), layer_3 = Dense(10 => 10, sin), layer_4 = Dense(10 => 10, sin)),  # 440 parameters
        ),
    ),
    layer_3 = Dense(10 => 1),           # 11 parameters
)         # Total: 2_371 parameters,
          #        plus 90 states, summarysize 192 bytes
```
