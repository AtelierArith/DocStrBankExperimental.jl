```
cliquetree([weights, ]graph;
    alg::PermutationOrAlgorithm=DEFAULT_ELIMINATION_ALGORITHM,
    snd::SupernodeType=DEFAULT_SUPERNODE_TYPE)
```

単純グラフのツリーデコレーションを構築します。グラフの頂点は、まずアルゴリズム `alg` によって計算されたフィル削減順列によって順序付けられます。結果として得られるデコレーションのサイズは、スーパーノードパーティション `snd` によって決まります。

```jldoctest
julia> using CliqueTrees

julia> graph = [
           0 1 0 0 0 0 0 0
           1 0 1 0 0 1 0 0
           0 1 0 1 0 1 1 1
           0 0 1 0 0 0 0 0
           0 0 0 0 0 1 1 0
           0 1 1 0 1 0 0 0
           0 0 1 0 1 0 0 1
           0 0 1 0 0 0 1 0
       ];

julia> label, tree = cliquetree(graph);

julia> tree
6-element CliqueTree{Int64, Int64}:
 [6, 7, 8]
 └─ [5, 7, 8]
    ├─ [1, 5]
    ├─ [3, 5, 7]
    │  └─ [2, 3]
    └─ [4, 5, 8]
```
