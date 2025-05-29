```
maybecold(y, labels=1:size(y,1))
```

Similar to `Flux.onecold` but when `y` contains `missing` values, `missing` is in the result as well.

Therefore, it is roughly the inverse operation of [`maybehot`](@ref) or [`maybehotbatch`](@ref).

# Examples

```jldoctest
julia> maybehot(:b, [:a, :b, :c])
3-element MaybeHotVector with eltype Bool:
 ⋅
 1
 ⋅

julia> maybecold(ans, [:a, :b, :c])
:b

julia> maybehot(missing, 1:3)
3-element MaybeHotVector with eltype Missing:
 missing
 missing
 missing

julia> maybecold(ans)
missing

julia> maybecold(maybehotbatch([missing, 2], 1:3))
2-element Vector{Union{Missing, Int64}}:
  missing
 2
```

See also: `Flux.onecold`, [`maybehot`](@ref), [`maybehotbatch`](@ref).
