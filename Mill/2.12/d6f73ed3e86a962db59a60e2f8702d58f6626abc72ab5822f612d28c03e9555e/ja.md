```
maybehot(l, labels)
```

`labels`の中で`l`の最初の出現を`1`に設定し、他のすべての要素を`0`に設定した[`MaybeHotVector`](@ref)を返します。

# 例

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

関連項目: [`maybehotbatch`](@ref), [`MaybeHotVector`](@ref), [`MaybeHotMatrix`](@ref).
