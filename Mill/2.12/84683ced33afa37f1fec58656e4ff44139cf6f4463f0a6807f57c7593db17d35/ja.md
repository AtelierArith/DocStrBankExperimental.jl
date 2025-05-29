```
maybecold(y, labels=1:size(y,1))
```

`Flux.onecold`に似ていますが、`y`に`missing`値が含まれている場合、結果にも`missing`が含まれます。

したがって、これはおおよそ[`maybehot`](@ref)または[`maybehotbatch`](@ref)の逆操作です。

# 例

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

参照: `Flux.onecold`, [`maybehot`](@ref), [`maybehotbatch`](@ref).
