```
insert_parents!(node::Node, template, <keyword arguments>)
insert_generations!(node::Node, template, <keyword arguments>)
insert_children!(node::Node, template, <keyword arguments>)
insert_siblings!(node::Node, template, <keyword arguments>)
```

Insert new nodes in the mtg following filters rules. It is important to note the function always return the root node, whether it is the old one or a new inserted one, so the user is encouraged to assign the results to an object.

Insert nodes programmatically in an MTG as:

  * new parents of the filtered nodes: `insert_parents!`
  * new children of the filtered nodes: `insert_children!`
  * new siblings of the filtered node: `insert_siblings!`
  * new children of the filtered nodes, but the previous children of the filtered node become

the children of the inserted node: `insert_generations!`

# Arguments

## Mandatory arguments

  * `node::Node`: The node to start at.
  * `template`:

      * A template [`NodeMTG`](@ref) or [`MutableNodeMTG`](@ref) used for the inserted node,
      * A NamedTuple with values for link, symbol, index, and scale
      * Or a function taking the node as input and returning said template
  * `attr`: Attributes for the node. Similarly to `template`, can be:

      * An attribute of the same type as of node attributes (*e.g.* a Dict or a NamedTuple)
      * A function to compute new attributes (should also return same type for the attributes)

## Keyword Arguments (filters)

  * `scale = nothing`: The scale at which to insert. Usually a Tuple-alike of integers.
  * `symbol = nothing`: The symbol at which to insert. Usually a Tuple-alike of Strings.
  * `link = nothing`: The link with at which to insert. Usually a Tuple-alike of Char.
  * `all::Bool = true`: Continue after the first insertion (`true`), or stop.
  * `filter_fun = nothing`: Any function taking a node as input, e.g. [`isleaf`](@ref) to decide

on which node the insertion will be based on.

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# Insert new Shoot nodes before all scale 2 nodes:
mtg = insert_parents!(mtg, MultiScaleTreeGraph.MutableNodeMTG("/", "Shoot", 0, 1), scale = 2)

mtg
```
