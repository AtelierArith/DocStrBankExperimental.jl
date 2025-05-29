```
classes(ops::AbstractVector{SymOperation{D}}, [cntr::Union{Char, Nothing}])
                                                -->  Vector{Vector{SymOperation{D}}}
```

Return the conjugacy classes of a group $G$ defined by symmetry operations `ops`.

## Definitions

Two elements $a$ and $b$ in $G$ are considered conjugate if there exists a $g ∈ G$ such that $gag^{-1} = b$. This defines an equivalence relation $\sim$, i.e., we say that $a \sim b$ if $a$ and $b$ are conjugate. The conjugacy classes of $G$ are the distinct equivalence classes that can be identified under this equivalence relation, i.e. the grouping of $G$ into subsets that are equivalent under conjugacy.

## Extended help

If `ops` describe operations in a crystal system that is not primitive (i.e., if its [`centering`](@ref) type is not `p` or `P`) but is presented in a conventional setting, the centering symbol `cntr` *must* be given. If `ops` is not in a centered crystal system, or if `ops` is already reduced to a primitive setting, `cntr` should be given as `nothing` (default behavior) or, alternatively, as `P` or `p` (depending on dimensionality).

A single-argument calls to `classes` with `SpaceGroup` or `LittleGroup` types will assume that `ops` is provided in a conventional setting, i.e., will forward the method call to `classes(ops, centering(ops, dim(ops)))`. To avoid this behavior (if `ops` was already reduced to a primitive setting prior to calling `classes`), `cntr` should be provided explicitly as `nothing`.
