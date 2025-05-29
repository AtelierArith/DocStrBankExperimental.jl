```
blockmodel(g, groups; by=identity)
```

`g` の `Graphs.AbstractGraph` から `Blockmodel` を作成し、グループメンバーシップのベクトル `groups` を使用します。`by` に渡される関数は、ブロックモデル内のグループを順序付けるために使用されます。

# 例

```julia
using Graphs, BlockmodelUtils

g = erdos_renyi(20, 0.1) 
gs = rand(['a', 'b'], 20) 
bm = blockmodel(g, gs)
```
