```
addchild!(p::Node, id::Int, MTG<:AbstractNodeMTG, attributes)
addchild!(p::Node, MTG<:AbstractNodeMTG, attributes)
addchild!(p::Node, MTG<:AbstractNodeMTG)
addchild!(p::Node, child::Node; force=false)
```

親ノード（`p`）に新しい子ノードを追加し、親ノードを親として追加します。子ノードを返します。

[`insert_child!`](@ref) も参照してください。または、親を渡すことができ、内部で `addchild!` を使用する直接の [`Node`](@ref) を参照してください。

# 例

```julia
# ルートノードを作成します：
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
