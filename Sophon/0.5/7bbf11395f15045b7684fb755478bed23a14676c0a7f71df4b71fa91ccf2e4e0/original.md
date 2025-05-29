```
ResNet(layer_sizes::NTuple{N, Int}, activation; outermost=true,
               init_weight=kaiming_uniform(activation),
               init_bias=zeros32,
               allow_fast_activation=false)
ResNet(in_dims::Int, out_dims::Int, activation::Function;
               hidden_dims::Int, num_layers::Int, outermost=true,
               init_weight=kaiming_uniform(activation),
               init_bias=zeros32,
               allow_fast_activation=false)
```

Create fully connected layers.

## Arguments

  * `layer_sizes`: Number of dimensions of each layer.
  * `hidden_dims`: Number of hidden dimensions.
  * `num_layers`: Number of layers.
  * `activation`: Activation function.

## Keyword Arguments

  * `outermost`: Whether to use activation function for the last layer. If `false`, the activation function is applied to the output of the last layer.
  * `init_weight`: Initialization method for the weights.
  * `allow_fast_activation`: If true, then certain activations can be approximated with a faster version. The new activation function will be given by NNlib.fast_act(activation)

## Example

```julia
julia> ResNet((1, 12, 24, 32), relu)
Chain(
    layer_1 = Dense(1 => 12, relu),     # 24 parameters
    layer_2 = SkipConnection(
        Dense(12 => 24, relu),          # 312 parameters
        +
    ),
    layer_3 = Dense(24 => 32),          # 800 parameters
)         # Total: 1_136 parameters,
          #        plus 0 states, summarysize 48 bytes.

julia> ResNet(1, 10, relu; hidden_dims=20, num_layers=3)
Chain(
    layer_1 = Dense(1 => 20, relu),     # 40 parameters
    layer_2 = SkipConnection(
        Dense(20 => 20, relu),          # 420 parameters
        +
    ),
    layer_3 = SkipConnection(
        Dense(20 => 20, relu),          # 420 parameters
        +
    ),
    layer_4 = Dense(20 => 10),          # 210 parameters
)         # Total: 1_090 parameters,
          #        plus 0 states, summarysize 64 bytes.
```
