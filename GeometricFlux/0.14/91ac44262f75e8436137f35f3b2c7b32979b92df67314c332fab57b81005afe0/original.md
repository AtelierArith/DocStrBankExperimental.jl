```
SAGEConv(in => out, σ=identity, aggr=mean; normalize=true, project=false,
         bias=true, num_sample=10, init=glorot_uniform)
```

SAmple and aggreGatE convolutional layer for GraphSAGE network.

# Arguments

  * `in`: The dimension of input features.
  * `out`: The dimension of output features.
  * `σ`: Activation function.
  * `aggr`: An aggregate function applied to the result of message function. `mean`, `max`,

`LSTM` and `GCNConv` are available.

  * `normalize::Bool`: Whether to normalize features across all nodes or not.
  * `project::Bool`: Whether to project, i.e. `Dense(in, in)`, before aggregation.
  * `bias`: Add learnable bias.
  * `num_sample::Int`: Number of samples for each node from their neighbors.
  * `init`: Weights' initializer.

# Examples

```jldoctest
julia> SAGEConv(1024=>256, relu)
SAGEConv(1024 => 256, relu, aggr=mean, normalize=true, #sample=10)

julia> SAGEConv(1024=>256, relu, num_sample=5)
SAGEConv(1024 => 256, relu, aggr=mean, normalize=true, #sample=5)

julia> MeanAggregator(1024=>256, relu, normalize=false)
SAGEConv(1024 => 256, relu, aggr=mean, normalize=false, #sample=10)

julia> MeanPoolAggregator(1024=>256, relu)
SAGEConv(1024 => 256, relu, project=Dense(1024 => 1024), aggr=mean, normalize=true, #sample=10)

julia> MaxPoolAggregator(1024=>256, relu)
SAGEConv(1024 => 256, relu, project=Dense(1024 => 1024), aggr=max, normalize=true, #sample=10)

julia> LSTMAggregator(1024=>256, relu)
SAGEConv(1024 => 256, relu, aggr=LSTMCell(1024 => 1024), normalize=true, #sample=10)
```

See also [`WithGraph`](@ref) for training layer with static graph and [`MeanAggregator`](@ref), [`MeanPoolAggregator`](@ref), [`MaxPoolAggregator`](@ref) and [`LSTMAggregator`](@ref).
