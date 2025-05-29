```
insert_parent!(node, template, attr_fun = node -> typeof(node_attributes(node))(), max_id = [max_id(node)])
insert_generation!(node, template, attr_fun = node -> typeof(node_attributes(node))(), max_id = [max_id(node)])
insert_child!(node, template, attr_fun = node -> typeof(node_attributes(node))(), max_id = [max_id(node)])
insert_sibling!(node, template, attr_fun = node -> typeof(node_attributes(node))(), max_id = [max_id(node)])
```

Insert a node in an MTG as:

  * a new parent of node: `insert_parent!`
  * a new child of node: `insert_child!`
  * a new sibling of node: `insert_sibling!`
  * a new child of node, but the children of node become the children of the inserted node:

`insert_generation!`

# Arguments

  * `node::Node`: The node from which to insert a node (as its parent, child or sibling).
  * `template`:

      * A template [`NodeMTG`](@ref) or [`MutableNodeMTG`](@ref) used for the inserted node,
      * A NamedTuple with values for link, symbol, index, and scale
      * Or a function taking the node as input and returning said template
  * `attr_fun`: A function to compute new attributes based on the filtered node. Must return

attribute values of the same type as the one used in other nodes from the MTG (*e.g.* Dict or NamedTuple). If you just need to pass attributes values to a node use `x -> your_values`.

  * `max_id::Vector{Int64}`: The maximum id of the nodes in the MTG as a vector of length one. It is incremented in the function,

and use by default the value from [`max_id`](@ref).

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

template = MultiScaleTreeGraph.MutableNodeMTG("/", "Shoot", 0, 1)
insert_parent!(mtg[1][1], template)
mtg

# The template can be a function that returns the template. For example a dummy example would
# be a function that uses the NodeMTG of the first child of the node:

insert_parent!(
    mtg[1][1],
    node -> (
        link = link(node[1]),
        symbol = symbol(node[1]),
        index = index(node[1]),
        scale = scale(node[1]))
    )
)
```
