```
probabilities(at::AliasTable{T}) -> Vector{T}
```

与えられた `AliasTable` から正確なサンプリング重みを回復します。返される値は、`at` が定数分布（例: `AliasTable([0,1,0])`）でない限り、`typemax(T)` よりも 1 大きく合計されます。この場合、重みは `typemax(T)` に合計されます。

参照: [`AliasTable`](@ref), [`AliasTables.sample`](@ref)

# 例

```jldoctest
julia> at = AliasTable([1, 3, 1])
AliasTable([0x3333333333333334, 0x9999999999999999, 0x3333333333333333])

julia> AliasTables.probabilities(at)
3-element Vector{UInt64}:
 0x3333333333333334
 0x9999999999999999
 0x3333333333333333

julia> AliasTables.probabilities(AliasTable([0, 1, 0]))
3-element Vector{UInt64}:
 0x0000000000000000
 0xffffffffffffffff
 0x0000000000000000
```
