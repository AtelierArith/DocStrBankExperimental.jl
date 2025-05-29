```
maybehotbatch(ls, labels)
```

Return a [`MaybeHotMatrix`](@ref) in which each column corresponds to one element of `ls` containing `1` at its first occurence in `labels` with all other elements set to `0`.

# Examples

```jldoctest
julia> maybehotbatch([:c, :a], [:a, :b, :c])
3×2 MaybeHotMatrix with eltype Bool:
 ⋅  1
 ⋅  ⋅
 1  ⋅

julia> maybehotbatch([missing, 2], 1:3)
3×2 MaybeHotMatrix with eltype Union{Missing, Bool}:
 missing  ⋅
 missing  1
 missing  ⋅
```

See also: [`maybehot`](@ref), [`MaybeHotMatrix`](@ref), [`MaybeHotVector`](@ref).
