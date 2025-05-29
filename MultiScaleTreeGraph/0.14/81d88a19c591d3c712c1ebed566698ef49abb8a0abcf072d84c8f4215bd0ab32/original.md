```
addchild!(p::Node, id::Int, MTG<:AbstractNodeMTG, attributes)
addchild!(p::Node, MTG<:AbstractNodeMTG, attributes)
addchild!(p::Node, MTG<:AbstractNodeMTG)
addchild!(p::Node, child::Node; force=false)
```

Add a new child to a parent node (`p`), and add the parent node as the parent. Returns the child node.

See also [`insert_child!`](@ref), or directly [`Node`](@ref) where we  can pass the parent, and it uses `addchild!` under the hood.

# Examples

```julia
# Create a root node:
mtg = MultiScaleTreeGraph.Node(
    NodeMTG("/", "Plant", 1, 1),
    Dict{Symbol,Any}()
)

roots = addchild!(
    mtg, 
    NodeMTG("+", "RootSystem", 1, 2)
)

stem = addchild!(
    mtg, 
    NodeMTG("+", "Stem", 1, 2)
)

phyto = addchild!(
    stem, 
    NodeMTG("/", "Phytomer", 1, 3)
)

mtg
```
