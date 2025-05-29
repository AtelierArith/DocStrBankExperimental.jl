```
Node(MTG<:AbstractNodeMTG)
Node(parent::Node, MTG<:AbstractNodeMTG)
Node(id::Int, MTG<:AbstractNodeMTG, attributes)
Node(id::Int, parent::Node, MTG<:AbstractNodeMTG, attributes)
Node(id::Int, parent::Node, children::Vector{Node}, MTG<:AbstractNodeMTG, attributes)
Node(
    id::Int,
    parent::Node,
    children::Vector{Node},
    MTG<:AbstractNodeMTG,
    attributes;
    traversal_cache
)
```

Type that defines an MTG node (*i.e.* an element) with:

  * `id`: The unique id of node (unique in the whole MTG)
  * `parent`: the parent node (if not the root node)
  * `children`: an optional array of children nodes
  * `MTG`: the MTG description, or encoding (see [`NodeMTG`](@ref) or

[`MutableNodeMTG`](@ref))

  * `attributes`: the node attributes, that can be anything but

usually a `Dict{String,Any}`

  * `traversal_cache`: a cache for the traversal, used by *e.g.* [`traverse`](@ref) to traverse more efficiently particular nodes in the MTG

The node is an entry point to a Mutli-Scale Tree Graph, meaning we can move through the MTG from any of its node. The root node is the node without parent. A leaf node is a node without any children. Root and leaf nodes are used with their computer science meaning throughout the package, not in the biological sense.

Note that it is possible to create a whole MTG using only the `Node` type, because it has methods to create a node as a child of another node (see example below). 

# Examples

```julia
mtg = Node(NodeMTG("/", "Plant", 1, 1))
internode = Node(mtg, NodeMTG("/", "Internode", 1, 2))
# Note that the node is created with a parent, so it is not necessary to add it as a child of the `mtg ` Node

mtg
```
