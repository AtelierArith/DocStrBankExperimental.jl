```
tree_from_leaves(leafnodes::Vector{Vector{Int}}, probs::Vector{Float64})
```

葉ノードの配列からツリーを構築し、（オプションで）対応する確率を指定します。

### 必須引数

`leafnodes` は葉ノードのセットを定義する配列の配列です。

### オプション引数

`probs` は葉ノードの確率の配列です。

### 例

```
(tree,prob) = tree_from_leaves([[1,1,1],[1,1,2],[1,2,1],[1,2,2]],[0.25,0.25,0.25,0.25])
tree = tree_from_leaves([[1,1,1],[1,1,2],[1,2,1],[1,2,2]])
```
