```
struct Treewidth{EL <: EliminationAlgorithm, GM} <: CodeOptimizer
Treewidth(; alg::EL = SafeRules(BT(), MMW{3}(), MF()), greedy_config::GM = GreedyMethod(nrepeat=1))
```

Tree width based solver. The solvers are implemented in [CliqueTrees.jl](https://algebraicjulia.github.io/CliqueTrees.jl/stable/) and [TreeWidthSolver.jl](https://github.com/ArrogantGao/TreeWidthSolver.jl). They include:

| Algorithm | Description                                  | Time Complexity | Space Complexity |
|:--------- |:-------------------------------------------- |:--------------- |:---------------- |
| `BFS`     | breadth-first search                         | O(m + n)        | O(n)             |
| `MCS`     | maximum cardinality search                   | O(m + n)        | O(n)             |
| `LexBFS`  | lexicographic breadth-first search           | O(m + n)        | O(m + n)         |
| `RCMMD`   | reverse Cuthill-Mckee (minimum degree)       | O(m + n)        | O(m + n)         |
| `RCMGL`   | reverse Cuthill-Mckee (George-Liu)           | O(m + n)        | O(m + n)         |
| `MCSM`    | maximum cardinality search (minimal)         | O(mn)           | O(n)             |
| `LexM`    | lexicographic breadth-first search (minimal) | O(mn)           | O(n)             |
| `AMF`     | approximate minimum fill                     | O(mn)           | O(m + n)         |
| `MF`      | minimum fill                                 | O(mn²)          | -                |
| `MMD`     | multiple minimum degree                      | O(mn²)          | O(m + n)         |

Detailed descriptions is available in the [CliqueTrees.jl](https://algebraicjulia.github.io/CliqueTrees.jl/stable/api/#Elimination-Algorithms).

# Fields

  * `alg::EL`: The algorithm to use for the treewidth calculation. Available elimination algorithms are listed above.
  * `greedy_config::GM`: The configuration for the greedy method.

# Example

```jldoctest
julia> optimizer = Treewidth();

julia> eincode = OMEinsumContractionOrders.EinCode([['a', 'b'], ['a', 'c', 'd'], ['b', 'c', 'e', 'f'], ['e'], ['d', 'f']], ['a'])
ab, acd, bcef, e, df -> a

julia> size_dict = Dict([c=>(1<<i) for (i,c) in enumerate(['a', 'b', 'c', 'd', 'e', 'f'])]...)
Dict{Char, Int64} with 6 entries:
  'f' => 64
  'a' => 2
  'c' => 8
  'd' => 16
  'e' => 32
  'b' => 4

julia> optcode = optimize_code(eincode, size_dict, optimizer)
ab, ab -> a
├─ fac, bcf -> ab
│  ├─ df, acd -> fac
│  │  ├─ df
│  │  └─ acd
│  └─ e, bcef -> bcf
│     ├─ e
│     └─ bcef
└─ ab
```
