```
ConfigsMin{K, BOUNDED, TREESTORAGE} <:AbstractProperty
ConfigsMin(K=Single; bounded=true, tree_storage=false)
```

Find configurations with smallest-K sizes.

  * The corresponding data type is inverted [`CountingTropical`](@ref)`{Float64,<:ConfigEnumerator}` if `K` is `Single` and inverted [`TruncatedPoly`](@ref)`{K,<:ConfigEnumerator}` if `K` is an integer.
  * Weighted constraint satisfaction problem is only supported if `K` is `Single`.

## Keyword Arguments

  * `bounded`, if it is true, use bounding trick (or boolean gradients) to reduce the working memory to store intermediate configurations.
  * `tree_storage`, if it is true, it uses more memory efficient tree-structure to store the configurations.
