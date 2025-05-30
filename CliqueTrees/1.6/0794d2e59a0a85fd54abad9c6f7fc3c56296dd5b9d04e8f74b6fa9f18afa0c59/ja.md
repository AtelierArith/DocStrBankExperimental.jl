```
MCSM <: EliminationAlgorithm

MCSM()
```

最大基数探索アルゴリズムの最小バリアント。

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

julia> alg = MCSM()
MCSM

julia> treewidth(graph; alg)
2
```

### 参考文献

  * Berry, Anne, et al. "最大基数探索によるグラフの最小三角化の計算。" *Algorithmica* 39 (2004): 287-298.
