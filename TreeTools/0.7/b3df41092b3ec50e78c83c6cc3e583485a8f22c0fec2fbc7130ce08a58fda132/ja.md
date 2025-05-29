```
prune!(tree, node; kwargs...)
prune!(tree, labels::AbstractArray)
prune!(tree, labels...)
```

`tree` から `node` を剪定します。`node` はラベルまたは `TreeNode` であることができます。`node` によって定義される部分木を `Tree` オブジェクトとして返し、`node` の前の祖先も返します。

ラベルのリストが提供されると、対応するノードの最も近い共通祖先 (MRCA) が剪定されます。

## kwargs

  * `remove_singletons`: 剪定後に木の中のシングルトン（子が1つの内部ノード）を削除します。デフォルトは `true` です。
  * `clade_only`: ラベルのリストが提供される場合、剪定する前にそれがクレードに対応しているかを確認します。デフォルトは `true` です。
  * `create_leaf`: `r` の祖先が子を1つだけ持つ（シングルトン）場合、`r` を剪定すると葉が作成されます。`create_leaf == :warn` の場合、警告が発生します。`create_leaf = false` の場合、エラーが発生します。`create_leaf = true` の場合、これは許可されます。デフォルト: `:warn`。

## 例

```jldoctest
using TreeTools # hide
tree = parse_newick_string("(A:1.,(B:1.,(X1:0.,X2:0.)X:5.)BX:1.)R;")
prune!(tree, ["X1", "X2"])
map(label, nodes(tree))

# 出力

3-element Vector{String}:
 "B"
 "A"
 "R"
```
