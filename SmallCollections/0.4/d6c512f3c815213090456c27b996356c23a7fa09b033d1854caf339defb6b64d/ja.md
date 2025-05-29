```
duplicate(v::V, i::Integer, x) where V <: AbstractCapacityVector{T} -> V
```

`v`の`i`番目のエントリを複製し、`i+1`の位置に挿入して新しいベクターを返します。

[`insert`](@ref)も参照してください。

# 例

```jldoctest
julia> v = SmallVector{8,Int8}(1:3)
3-element SmallVector{8, Int8}:
 1
 2
 3

julia> duplicate(v, 2)
4-element SmallVector{8, Int8}:
 1
 2
 2
 3
```
