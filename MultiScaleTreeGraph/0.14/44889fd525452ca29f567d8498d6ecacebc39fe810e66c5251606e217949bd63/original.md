```
get_node(node::Node, id::Int)
```

Get a node in an mtg by id.

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)
node_6_2 = get_node(mtg, 6)
```
