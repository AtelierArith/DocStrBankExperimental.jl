```
support(v::AbstractCapacityVector) -> SmallBitSet
```

`v`の非ゼロ要素のインデックスを持つ`SmallBitSet`を返します。

[`SmallBitSet`](@ref)も参照してください。

# 例

```jldoctest
julia> v = SmallVector{8,Int8}([1, 0, 2, 0, 0, 3]);

julia> support(v)
SmallBitSet{UInt64} with 3 elements:
  1
  3
  6
```
