```julia
struct ImplicitTree{T<:Integer}
```

`num_leaves` 要素の暗黙の二分木で、ノードは幅優先探索に従ってラベル付けされます。

# メソッド

```
ImplicitTree(num_leaves::Integer)
ImplicitTree{T}(num_leaves::Integer)
```

# フィールド

  * `levels::Integer`: 木のレベル数。
  * `real_leaves::Integer`: 実際の葉の数 - すなわち、木が構築された要素の数。
  * `real_nodes::Integer`: 木の実際のノードの総数。
  * `virtual_leaves::Integer`: 完全な二分木を持つために底レベルで必要な仮想葉の数。
  * `virtual_nodes::Integer`: 完全な二分木に必要な木の仮想ノードの総数。

# 例

```julia
julia> using ImplicitBVH

# 5つの幾何要素（例：バウンディングボックス）が与えられたとき、次のような暗黙の木を構築します
# 実際の葉が暗黙のインデックス8-12にあり、さらに3つの仮想葉があります。
#         ノード & 葉                木のレベル
#               1                       1
#       2               3               2
#   4       5       6        7v         3
# 8   9   10 11   12 13v  14v  15v      4
julia> tree = ImplicitTree(5)
ImplicitTree{Int64}
  levels: Int64 4
  real_leaves: Int64 5
  real_nodes: Int64 11
  virtual_leaves: Int64 3
  virtual_nodes: Int64 4

# 実際のノードの実メモリインデックスを計算することで、仮想ノードのための余分なパディングなしで
# すべての木のノードを連続ベクターに保持できます。例えば、ノード8の実メモリインデックスは
# 仮想のノード7をスキップします：
julia> memory_index(tree, 8)
7

# 特定のレベルの実ノードのインデックスの範囲を取得できます
julia> level_indices(tree, 3)
(4, 6)

# そして、特定の暗黙のインデックスのノードが仮想であるかどうかを確認できます
julia> isvirtual(tree, 6)
false

julia> isvirtual(tree, 7)
true
```
