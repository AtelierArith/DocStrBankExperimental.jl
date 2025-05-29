```
GATv2Conv(in => out, σ=identity; heads=1, concat=true,
          init=glorot_uniform, negative_slope=0.2)
```

Graph attentional layer v2.

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `σ`: Activation function.
  * `heads`: Number attention heads
  * `concat`: Concatenate layer output or not. If not, layer output is averaged.
  * `negative_slope::Real`: Keyword argument, the parameter of LeakyReLU.

# Examples

```jldoctest
julia> GATv2Conv(1024=>256, relu)
GATv2Conv(1024=>256, relu, heads=1, concat=true, LeakyReLU(λ=0.2))

julia> GATv2Conv(1024=>256, relu, heads=4)
GATv2Conv(1024=>1024, relu, heads=4, concat=true, LeakyReLU(λ=0.2))

julia> GATv2Conv(1024=>256, relu, heads=4, concat=false)
GATv2Conv(1024=>1024, relu, heads=4, concat=false, LeakyReLU(λ=0.2))

julia> GATv2Conv(1024=>256, relu, negative_slope=0.1f0)
GATv2Conv(1024=>256, relu, heads=1, concat=true, LeakyReLU(λ=0.1))
```

See also [`WithGraph`](@ref) for training layer with static graph.
