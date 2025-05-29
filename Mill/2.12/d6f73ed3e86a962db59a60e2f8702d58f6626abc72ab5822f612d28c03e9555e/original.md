```
maybehot(l, labels)
```

Return a [`MaybeHotVector`](@ref) where the first occurence of `l` in `labels` is set to `1` and all other elements are set to `0`.

# Examples

```jldoctest
julia> maybehot(:b, [:a, :b, :c])
3-element MaybeHotVector with eltype Bool:
 ⋅
 1
 ⋅

julia> maybehot(missing, 1:3)
3-element MaybeHotVector with eltype Missing:
 missing
 missing
 missing
```

See also: [`maybehotbatch`](@ref), [`MaybeHotVector`](@ref), [`MaybeHotMatrix`](@ref).
