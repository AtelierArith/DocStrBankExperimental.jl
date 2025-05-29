```
maybehotbatch(ls, labels)
```

`ls`の各要素に対応する列を持ち、`labels`内で最初に出現する位置に`1`を持ち、他のすべての要素は`0`に設定された[`MaybeHotMatrix`](@ref)を返します。

# 例

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

参照: [`maybehot`](@ref), [`MaybeHotMatrix`](@ref), [`MaybeHotVector`](@ref).
