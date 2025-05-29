```
eliminationtree([weights, ]graph;
    alg::PermutationOrAlgorithm=DEFAULT_ELIMINATION_ALGORITHM)
```

単純グラフの[木深さ分解](https://en.wikipedia.org/wiki/Tr%C3%A9maux_tree)を構築します。

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

julia> label, tree = eliminationtree(graph);

julia> tree
8-element Tree{Int64}:
 8
 └─ 7
    ├─ 5
    └─ 6
       ├─ 1
       ├─ 3
       │  └─ 2
       └─ 4
```
