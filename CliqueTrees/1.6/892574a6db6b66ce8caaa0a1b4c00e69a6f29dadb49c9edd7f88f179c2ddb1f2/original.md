```
ND{A, D} <: EliminationAlgorithm

ND(alg::EliminationAlgorithm, dis::DissectionAlgorithm; limit=200, level=6)

ND(alg::EliminationAlgorithm; limit=200, level=6)

ND(; limit=200, level=6)
```

The [nested dissection algorithm](https://en.wikipedia.org/wiki/Nested_dissection).

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

### Parameters

  * `alg`: elimination algorithm
  * `dis`: dissection algorithm
  * `limit`: smallest subgraph
  * `level`: maximum depth
