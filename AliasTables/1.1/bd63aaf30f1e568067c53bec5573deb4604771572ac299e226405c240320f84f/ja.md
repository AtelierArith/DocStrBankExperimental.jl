```
set_weights!(at::AliasTable, weights::AbstractVector{<:Real})
```

`at`の重みを`weights`に設定し、`at`を返します。

GC管理のアロケーションは行いません。

# 例

```jldoctest
julia> at = AliasTable([1, 3, 1])
AliasTable([0x3333333333333334, 0x9999999999999999, 0x3333333333333333])

julia> at === AliasTables.set_weights!(at, [1, 2, 1])
true

julia> at
AliasTable([0x4000000000000000, 0x8000000000000000, 0x4000000000000000])
```
