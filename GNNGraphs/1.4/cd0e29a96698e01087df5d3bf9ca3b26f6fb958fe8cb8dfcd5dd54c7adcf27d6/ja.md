```
remove_nodes(g::GNNGraph, nodes_to_remove::AbstractVector)
```

指定されたノードとそれに関連するエッジをGNNGraphから削除します。この操作は、残りのノードのインデックスを再インデックス化し、1から始まる連続したノードインデックスのシーケンスを維持します。同様に、削除されたノードに接続されていたエッジの削除を考慮して、エッジも再インデックス化されます。

# 引数

  * `g`: ノード（およびそのエッジ）を削除する入力グラフ。
  * `nodes_to_remove`: 削除するノードインデックスのベクター。

# 戻り値

指定されたノードとこれらのノードに関連するすべてのエッジが削除された新しいGNNGraph。

# 例

```julia
using GNNGraphs

g = GNNGraph([1, 1, 2, 2, 3], [2, 3, 1, 3, 1])

# 例えば、インデックス2と3のノードを削除
g_new = remove_nodes(g, [2, 3])

# g_newにはノード2と3、およびこれらのノードに接続されていたエッジは含まれていません。
println(g_new)
```
