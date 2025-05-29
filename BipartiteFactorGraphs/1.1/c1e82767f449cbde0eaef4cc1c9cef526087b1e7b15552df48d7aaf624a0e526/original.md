```
BipartiteFactorGraph
```

A type-stable bipartite undirected factor graph implementation that stores data for variables, factors, and edges. Users are responsible for maintaining the bipartite structure.

After the graph is constructed, the user can use `Graphs.is_bipartite(graph.graph)` to check if the graph is actually bipartite. Certain functions may work incorrectly and produce unexpected results if the underlying graph is not bipartite.

# Fields

  * `graph`: The underlying graph structure
  * `variable_data`: A dictionary of data for variable nodes where the keys are elements of type `Int` and the values are of type `TVar`
  * `factor_data`: A dictionary of data for factor nodes where the keys are elements of type `Int` and the values are of type `TFac`
  * `edge_data`: A dictionary of data for edges between variables and factors where the keys are elements of type `UnorderedPair` and the values are of type `E`

!!! note
    Edge data keys are stored as `UnorderedPair`s to avoid duplicate entries or access errors.  This means that `get_edge_data(g, v1, v2)` is equivalent to `get_edge_data(g, v2, v1)`. This also implies that the graph is undirected.


To construct an empty BipartiteFactorGraph with specified variable, factor and edge data types use the following constructor:

```julia
BipartiteFactorGraph(::Type{TVar}, ::Type{TFac}, ::Type{E}, dict_type::Type{D}=Dict) where {TVar,TFac,E,D}
```

# Arguments

  * `TVar`: The type of the variable data
  * `TFac`: The type of the factor data
  * `E`: The type of the edge data
  * `dict_type`: The type of the dictionary used to store the variable, factor and edge data (defaults to Base.Dict)

As an alternative to the constructor, you can use `BipartiteFactorGraph()` as an alias to `BipartiteFactorGraph(Any, Any, Any, Dict)`.

# Example

```jldoctest
julia> g = BipartiteFactorGraph(Int, Float64, String, Dict)
BipartiteFactorGraph{Int64, Float64, String} with 0 variables, 0 factors, and 0 edges

julia> add_variable!(g, 1);

julia> add_factor!(g, 2.0);

julia> add_edge!(g, 1, 2, "Hello");

julia> g
BipartiteFactorGraph{Int64, Float64, String} with 1 variables, 1 factors, and 1 edges
```
