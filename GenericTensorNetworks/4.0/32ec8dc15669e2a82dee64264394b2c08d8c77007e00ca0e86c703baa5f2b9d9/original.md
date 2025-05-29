```
ConfigsAll{TREESTORAGE} <:AbstractProperty
ConfigsAll(; tree_storage=false)
```

Find all valid configurations, e.g. for [`IndependentSet`](@ref) problem, it is finding all independent sets.

  * The corresponding data type is [`ConfigEnumerator`](@ref).
  * Weights do not take effect.

## Keyword Arguments

  * `tree_storage`, if it is true, it uses more memory efficient tree-structure to store the configurations.
