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

MTGノード（*すなわち* 要素）を定義する型で、以下を持ちます：

  * `id`: ノードの一意のID（MTG全体で一意）
  * `parent`: 親ノード（ルートノードでない場合）
  * `children`: 子ノードのオプションの配列
  * `MTG`: MTGの説明またはエンコーディング（[`NodeMTG`](@ref) または

[`MutableNodeMTG`](@ref)を参照）

  * `attributes`: ノードの属性で、何でも可能ですが通常は `Dict{String,Any}`
  * `traversal_cache`: トラバーサルのためのキャッシュで、*例として* [`traverse`](@ref)がMTG内の特定のノードをより効率的にトラバースするために使用します

ノードはマルチスケールツリーグラフへのエントリーポイントであり、MTGの任意のノードを通じて移動できます。ルートノードは親を持たないノードです。リーフノードは子を持たないノードです。ルートノードとリーフノードは、パッケージ全体でコンピュータサイエンスの意味で使用され、生物学的な意味ではありません。

`Node`型のみを使用して全体のMTGを作成することが可能であることに注意してください。なぜなら、他のノードの子としてノードを作成するためのメソッドがあるからです（以下の例を参照）。

# 例

```julia
mtg = Node(NodeMTG("/", "Plant", 1, 1))
internode = Node(mtg, NodeMTG("/", "Internode", 1, 2))
# ノードは親と共に作成されるため、`mtg`ノードの子として追加する必要はありません

mtg
```
