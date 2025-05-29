```
ND{A, D} <: EliminationAlgorithm

ND(alg::EliminationAlgorithm, dis::DissectionAlgorithm; limit=200, level=6)

ND(alg::EliminationAlgorithm; limit=200, level=6)

ND(; limit=200, level=6)
```

[nested dissection algorithm](https://en.wikipedia.org/wiki/Nested_dissection) の説明。

```julia-repl
julia> using CliqueTrees, Metis

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

julia> alg = ND(MF(), METISND(); limit=0, level=2)
ND{MF, METISND}:
    MF
    METISND:
        seed: -1
        ufactor: -1
    limit: 0
    level: 2

julia> treewidth(graph; alg)
2
```

### パラメータ

  * `alg`: 排除アルゴリズム
  * `dis`: 切断アルゴリズム
  * `limit`: 最小サブグラフ
  * `level`: 最大深さ
