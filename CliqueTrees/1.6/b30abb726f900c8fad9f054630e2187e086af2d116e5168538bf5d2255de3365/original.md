```
SafeRules{A, L, U} <: EliminationAlgorithm

SafeRules(alg::EliminationAlgorithm, lb::WidthOrAlgorithm, ub::EliminationAlgororithm)

SafeRules()
```

Preprocess a graph using safe reduction rules. The algorithm `lb` is used to compute a lower bound to the treewidth; better lower bounds allow the algorithm to perform more reductions.

```julia-repl
julia> using CliqueTrees, TreeWidthSolver

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

julia> alg1 = BT()
BT

julia> alg2 = SafeRules(BT(), MMW(), MF())
SafeRules{BT, MMW, MF}:
    BT
    MMW
    MF

julia> @time treewidth(graph; alg=alg1) # slow
  0.000177 seconds (1.41 k allocations: 90.031 KiB)
2

julia> @time treewidth(graph; alg=alg2) # fast
  0.000044 seconds (282 allocations: 15.969 KiB)
2
```

### Parameters

  * `alg`: elimination algorithm
  * `lb`: lower bound algorithm (used to lower bound the treiwidth)
  * `ub`: elimination algorithm (used to upper bound the treewidth)

### References

  * Bodlaender, Hans L., et al. "Pre-processing for triangulation of probabilistic networks." (2001).
  * Bodlaender, Hans L., Arie M.C.A. Koster, and Frank van den Eijkhof. "Preprocessing rules for triangulation of probabilistic networks." *Computational Intelligence* 21.3 (2005): 286-305.
  * van den Eijkhof, Frank, Hans L. Bodlaender, and Arie M.C.A. Koster. "Safe reduction rules for weighted treewidth." *Algorithmica* 47 (2007): 139-158.
