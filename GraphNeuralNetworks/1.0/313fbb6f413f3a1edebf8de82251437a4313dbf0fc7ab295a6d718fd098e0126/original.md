```
DConv(ch::Pair{Int, Int}, k::Int; init = glorot_uniform, bias = true)
```

Diffusion convolution layer from the paper [Diffusion Convolutional Recurrent Neural Networks: Data-Driven Traffic Forecasting](https://arxiv.org/pdf/1707.01926).

# Arguments

  * `ch`: Pair of input and output dimensions.
  * `k`: Number of diffusion steps.
  * `init`: Weights' initializer. Default `glorot_uniform`.
  * `bias`: Add learnable bias. Default `true`.

# Examples

```
julia> g = GNNGraph(rand(10, 10), ndata = rand(Float32, 2, 10));

julia> dconv = DConv(2 => 4, 4)
DConv(2 => 4, 4)

julia> y = dconv(g, g.ndata.x);

julia> size(y)
(4, 10)
```
