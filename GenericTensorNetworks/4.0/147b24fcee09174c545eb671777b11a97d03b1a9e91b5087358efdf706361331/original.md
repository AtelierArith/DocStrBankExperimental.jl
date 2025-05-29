```
ConfigsMax{K, BOUNDED, TREESTORAGE} <:AbstractProperty
ConfigsMax(K=Single; bounded=true, tree_storage=true)
```

Find configurations with largest-K sizes, e.g. for [`IndependentSet`](@ref) problem, it is finding all independent sets of sizes $\alpha(G), \alpha(G)-1, \ldots, \alpha(G)-K+1$.

  * The corresponding data type is [`CountingTropical`](@ref)`{Float64,<:ConfigEnumerator}` if `K` is `Single` and [`TruncatedPoly`](@ref)`{K,<:ConfigEnumerator}` if `K` is an integer.
  * Weighted constraint satisfaction problem is only supported if `K` is `Single`.

## Keyword Arguments

  * `bounded`, if it is true, use bounding trick (or boolean gradients) to reduce the working memory to store intermediate configurations.
  * `tree_storage`, if it is true, it uses more memory efficient tree-structure to store the configurations.
