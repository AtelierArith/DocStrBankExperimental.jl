```
GATConv(in => out, σ=identity; heads=1, concat=true,
        init=glorot_uniform, bias=true, negative_slope=0.2)
```

Graph attentional layer.

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `bias::Bool`: Keyword argument, whether to learn the additive bias.
  * `σ`: Activation function.
  * `heads`: Number attention heads
  * `concat`: Concatenate layer output or not. If not, layer output is averaged.
  * `negative_slope::Real`: Keyword argument, the parameter of LeakyReLU.

# Examples

```jldoctest
julia> GATConv(1024=>256, relu)
GATConv(1024=>256, relu, heads=1, concat=true, LeakyReLU(λ=0.2))

julia> GATConv(1024=>256, relu, heads=4)
GATConv(1024=>1024, relu, heads=4, concat=true, LeakyReLU(λ=0.2))

julia> GATConv(1024=>256, relu, heads=4, concat=false)
GATConv(1024=>1024, relu, heads=4, concat=false, LeakyReLU(λ=0.2))

julia> GATConv(1024=>256, relu, negative_slope=0.1f0)
GATConv(1024=>256, relu, heads=1, concat=true, LeakyReLU(λ=0.1))
```

See also [`WithGraph`](@ref) for training layer with static graph.
