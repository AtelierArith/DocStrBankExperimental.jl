```
sankey(connections; kwargs...)
```

Plots a sankey diagram from the `(source, target, weight)` entries in `connections`.

Specific attributes to `sankey` are:

  * `compact = true`: Reduces the amount of vertical space between nodes in each layer.
  * `fontsize = theme(scene, :fontsize)`: Sets the font size of the node labels.
  * `nodelabels = nothing`: Places labels under the nodes with the corresponding indices.
  * `nodecolor = :gray30`: Sets a color for each node or all nodes if only one color is provided.
  * `linkcolor = (:gray30, 0.2)`: Sets a color for each link or all links if only one color is provided.
  * `forceorder = Pair{Int,Int}[]`: Changes the order of nodes in the same layer(s). Can be `[6 => 1]` (node 6 before 1), or `:reverse` (reverse within all layers).

## Example

```julia
using CairoMakie, SankeyMakie
connections = [(1, 2, 10), (1, 3, 15), (3, 4, 5)]
sankey(connections; nodelabels = ["A", "B", "C", "D"])
```
