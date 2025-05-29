```
AMF <: EliminationAlgorithm

AMF(; speed=1)
```

近似最小充填アルゴリズム。

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

julia> alg = AMF(; speed=2)
AMF:
    speed: 2

julia> treewidth(graph; alg)
2
```

### パラメータ

  * `speed`: 充填近似戦略（`1`、`2`、または`3`）

### 参考文献

  * Rothberg, Edward, and Stanley C. Eisenstat. "Node selection strategies for bottom-up sparse matrix ordering." SIAM Journal on Matrix Analysis and Applications 19.3 (1998): 682-695.
