```
WithGraph([g], layer; dynamic=nothing)
```

Train GNN layers with static graph.

# Arguments

  * `g`: If a `FeaturedGraph` is given, a fixed graph is used to train with.
  * `layer`: A GNN layer.
  * `dynamic`: If a function is given, it enables dynamic graph update by constructing

dynamic graph through given function within layers.

# Example

```jldoctest
julia> using GraphSignals, GeometricFlux

julia> adj = [0 1 0 1;
              1 0 1 0;
              0 1 0 1;
              1 0 1 0];

julia> fg = FeaturedGraph(adj);

julia> gc = WithGraph(fg, GCNConv(1024=>256))  # graph preprocessed by adding self loops
WithGraph(Graph(#V=4, #E=8), GCNConv(1024 => 256))

julia> WithGraph(fg, Dense(10, 5))
Dense(10 => 5)      # 55 parameters

julia> model = Chain(
           GCNConv(32=>32),
           gc,
       );

julia> WithGraph(fg, model)
Chain(
  WithGraph(
    GCNConv(32 => 32),                  # 1_056 parameters
  ),
  WithGraph(
    GCNConv(1024 => 256),               # 262_400 parameters
  ),
)         # Total: 4 trainable arrays, 263_456 parameters,
          # plus 2 non-trainable, 32 parameters, summarysize 1.006 MiB.
```
