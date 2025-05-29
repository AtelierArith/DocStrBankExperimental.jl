```
sankey(src, dst, weights; kwargs..., plotattributes...)
sankey(g::AbstractMetaGraph; kwargs..., plotattributes...)
```

Plot a sankey diagram.

In addition to [Plots.jl attributes](http://docs.juliaplots.org/latest/attributes/) the following keyword arguments are supported.

| Keyword argument |             Default value |                                                                                                                                                                                                                                 Options |
| ----------------:| -------------------------:| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `node_labels` |                 `nothing` |                                                                                                                                                                                                              `AbstractVector{<:String}` |
|    `node_colors` |                 `nothing` |                                            Vector of [color specifications supported by Plots.jl](http://docs.juliaplots.org/latest/colors/) or [color palette](http://docs.juliaplots.org/latest/generated/colorschemes/#ColorPalette) |
|     `edge_color` |                   `:gray` | Plots.jl supported [color](http://docs.juliaplots.org/latest/colors/), color selection from connected nodes with `:src`, `:dst`, `:gradient`, or an `AbstractDict{Tuple{Int, Int}, Any}` where `edge_color[(src, dst)]` maps to a color |
| `label_position` |                 `:inside` |                                                                                                                                                                              `:legend`, `:node`, `:left`, `:right`, `:top` or `:bottom` |
|     `label_size` |                       `8` |                                                                                                                                                                                                                                   `Int` |
|        `compact` |                   `false` |                                                                                                                                                                                                                                  `Bool` |
|    `force_layer` | `Vector{Pair{Int,Int}}()` |                                                                                                                                       Vectors of Int pairs specifying the layer for every node e.g. `[4=>2]` to force node 4 in layer 3 |
|    `force_order` | `Vector{Pair{Int,Int}}()` |                                                                                                       Vectors of Int pairs specifying the node ordering in each layer e.g. `[1=>2]` to specify node 1 preceeds node 2 in the same layer |
