```
MCS <: EliminationAlgorithm

MCS()
```

最大カーディナリティ探索アルゴリズム。

```julia-repl
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

julia> alg = MCS()
MCS

julia> treewidth(graph; alg)
3
```

### 参考文献

  * Tarjan, Robert E., and Mihalis Yannakakis. "グラフの和音性をテストし、ハイパーグラフの非循環性をテストし、非循環ハイパーグラフを選択的に削減するための単純な線形時間アルゴリズム。" *SIAM Journal on Computing* 13.3 (1984): 566-579.
