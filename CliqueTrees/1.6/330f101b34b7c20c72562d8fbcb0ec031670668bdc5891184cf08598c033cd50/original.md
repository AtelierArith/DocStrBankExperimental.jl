```
SafeSeparators{M, A} <: EliminationAlgorithm

SafeSeparators(alg::EliminationAlgorithm, min::PermutationOrAlgorithm)

SafeSeparators(alg::EliminationAlgorithm)

SafeSeparators()
```

Apple an elimination algorithm to the atoms of an almost-clique separator decomposition. The algorithm `min` is used to compute the decomposition.

!!! warning
    The algorithm `min` must compute a *minimimal* ordering. This property is guaranteed by the following algorithms:

      * [`MCSM`](@ref)
      * [`LexM`](@ref)
      * [`MinimalChordal`](@ref)


### Parameters

  * `alg`: elimination algorithm
  * `min`: minimal elimination algorithm

### References

  * Bodlaender, Hans L., and Arie MCA Koster. "Safe separators for treewidth." *Discrete Mathematics* 306.3 (2006): 337-350.
  * Tamaki, Hisao. "A heuristic for listing almost-clique minimal separators of a graph." arXiv preprint arXiv:2108.07551 (2021).
