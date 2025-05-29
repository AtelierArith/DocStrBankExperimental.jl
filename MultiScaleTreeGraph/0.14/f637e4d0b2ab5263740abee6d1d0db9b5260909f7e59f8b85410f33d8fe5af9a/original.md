```
cache_nodes!(node; scale=nothing, symbol=nothing, link=nothing, filter_fun=nothing, overwrite=false)
```

Cache the nodes of the mtg based on the filters that would be applied to a traversal. This is used automatically when traversing using [`traverse!`](@ref) or [`transform!`](@ref).

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))), "test", "files", "simple_plant.mtg")
mtg = read_mtg(file, Dict)

# Cache all leaf nodes:
cache_nodes!(mtg, symbol="Leaf")

# Cached nodes are stored in the traversal_cache field of the mtg (here, the two leaves):
@test MultiScaleTreeGraph.node_traversal_cache(mtg)["_cache_c0bffb8cc8a9b075e40d26be9c2cac6349f2a790"] == [get_node(mtg, 5), get_node(mtg, 7)]

# Then you can use the cached nodes in a traversal:
traverse(mtg, x -> symbol(x), symbol="Leaf") == ["Leaf", "Leaf"]
```
