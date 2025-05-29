```
abstract type AbstractLocalIndices
```

Abstract type representing the *local*, *own*, and *ghost* indices in a part of a partition of a range `1:n` with length `n`.

# Notation

Let `1:n` be an integer range with length `n`. We denote the indices in `1:n` as the  *global* indices. Let us consider a partition of `1:n`. The indices in a part  in the partition are called the *own* indices of this part. I.e., each part *owns* a subset of `1:n`. All these subsets are disjoint. Let us assume that each part is equipped with a second set of indices called the *ghost* indices.  The set of ghost indices in a given part is an arbitrary subset of the global indices `1:n` that are owned by other parts. The union of the own and ghost indices is referred to as the *local* indices of this part. The sets of local indices might overlap between the different parts.

The sets of own, ghost, and local indices are stored using vector-like containers in concrete implementations of `AbstractLocalIndices`. This equips them with a certain order. The `i`-th own index in a part is defined as the one being stored at index `i` in the array that contains the own indices in this part (idem for ghost and local indices). The map between indices in these ordered index sets are given by functions such as [`local_to_global`](@ref), [`own_to_local`](@ref) etc.

# Supertype hierarchy

```
AbstractLocalIndices <: AbstractVector{Int}
```
