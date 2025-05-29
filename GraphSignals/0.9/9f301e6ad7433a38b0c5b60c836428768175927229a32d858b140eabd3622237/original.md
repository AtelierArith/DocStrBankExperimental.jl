```
FeaturedSubgraph(fg, nodes)
```

Construct a lightweight subgraph over a `FeaturedGraph`.

# Arguments

  * `fg::AbstractFeaturedGraph`: A base featured graph to construct a subgraph.
  * `nodes::AbstractVector`: It specifies nodes to be reserved from `fg`.

# Usage

```
julia> using GraphSignals

julia> g = [[2,3], [1,4,5], [1], [2,5], [2,4]];

julia> fg = FeaturedGraph(g)
FeaturedGraph:
	Undirected graph with (#V=5, #E=5) in adjacency matrix

julia> subgraph(fg, [1,2,3])
FeaturedGraph:
	Undirected graph with (#V=5, #E=5) in adjacency matrix
	Subgraph:	nodes([1, 2, 3])
```

See also [`subgraph`](@ref) for syntax sugar.
