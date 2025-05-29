```
prune!(node)
```

Prune a tree at `node`, *i.e.* delete the entire sub-tree starting at `node` (including it).

Returns an error if the node is a root, or the parent node of the (deleted) node.

# Examples

```julia
using MultiScaleTreeGraph
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

prune!(get_node(mtg, 6))

mtg
```
