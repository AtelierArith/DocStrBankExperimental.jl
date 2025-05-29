```
@mutate_node!(node, args...)
```

Mutate a single node in place.

# Arguments

  * `node`: the node to mutate
  * `args...`: The computations to apply to the node (see examples)

# See also

[`@mutate_mtg!`](@ref) to mutate all nodes of an mtg.

# Examples

```julia
# Importing an mtg from the package:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# Compute a new attribute with the scales and add 2 to its values:
@mutate_node!(mtg, scaling = node.scales .+ 2)

# The computation is only applied to the root node. To apply it to all nodes,
# see @mutate_mtg!

# Compute several new attributes, some based on others:
@mutate_node!(mtg, x = length(node_id(node)), y = node.x + 2, z = sum(node.y))

# We can also use it without parenthesis:

@mutate_node! mtg x = length(node_id(node))
```
