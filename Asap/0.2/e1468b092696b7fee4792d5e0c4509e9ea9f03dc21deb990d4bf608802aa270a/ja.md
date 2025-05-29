```
Element(nodes::Vector{Node}, nodeIndex::Vector{Int64}, section::Section, id::Symbol = nothing; release = :fixedfixed)
Element(nodeStart::Node, nodeEnd::Node, section::Section, id = :element; release = :fixedfixed)
```

オプションの `id` タグを持つフレーム要素を作成します。

# 例

```julia-repl
julia> Element(nodes, [1,2], sec)
julia> Element(node1, node2, sec, :groundfloor_element)
```

# オプション引数 `release`

このプロパティは、要素の端に関してノードの自由度（DOF）を切り離すことを可能にします。

## 利用可能なリリース:

  * :fixedfixed (デフォルト) - すべてのDOFはノードに結びついています
  * :fixedfree - 回転DOFは端ノードで解放されます
  * :freefixed - 回転DOFは開始ノードで解放されます
  * :freefree - すべての回転DOFが解放されます（トラス要素）
  * :joist - ねじりを除くすべての回転DOFが解放されます

## 例

```julia-repl
julia> Element(nodes, [1,2], sec; release = :fixedfree)
```
