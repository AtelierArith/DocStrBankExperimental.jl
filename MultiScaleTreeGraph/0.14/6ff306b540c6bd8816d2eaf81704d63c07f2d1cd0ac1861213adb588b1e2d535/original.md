delete_nodes!(mtg::Node,<keyword arguments>)

Delete nodes in mtg following filters rules.

# Arguments

## Mandatory arguments

  * `node::Node`: The node to start at.

## Keyword Arguments (filters)

  * `scale = nothing`: The scale to delete. Usually a Tuple-alike of integers.
  * `symbol = nothing`: The symbol to delete. Usually a Tuple-alike of Strings.
  * `link = nothing`: The link with the previous node to delete. Usually a Tuple-alike of Char.
  * `all::Bool = true`: Continue after the first deletion (`true`), or stop?
  * `filter_fun = nothing`: Any filtering function taking a node as input, e.g. [`isleaf`](@ref)

to decide whether to delete a node or not.

  * `child_link_fun = new_child_link`: a function that takes the child node of a deleted node

as input and returns its new link (see details).

# Notes

1. The function is acropetal, meaning it will apply the deletion from leaves to the root to ensure

that one pass is enough and we don't repeat the process of visiting already visited children.

2. The function does not do anything fancy, it let the user take care of its own rules when

deleting nodes, except for the link (see below).

3. The package provides some pre-made functions for filtering. See for example [`is_segment!`](@ref)

to re-compute the mtg at a given scale to have only nodes at branching points. This is often used to match automatic reconstructions from *e.g.* LiDAR point cloud with manual measurements.

4. The default function used for `child_link_fun` is [`new_child_link`](@ref), which tries to be

clever considering the parent and child links. See its help page for more information. If the link shouldn't be modified, use the `link` function instead.

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

delete_nodes!(mtg, scale = 2) # Will remove all nodes of scale 2

# Delete the leaves:
delete_nodes!(mtg, symbol = "Leaf")
# Delete the leaves and internodes:
delete_nodes!(mtg, symbol = ("Leaf","Internode"))
```
