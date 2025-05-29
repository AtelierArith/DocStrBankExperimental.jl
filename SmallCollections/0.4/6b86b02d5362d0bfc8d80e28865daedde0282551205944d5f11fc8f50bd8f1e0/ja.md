```
support(v::AbstractFixedVector) -> SmallBitSet
```

`v`の非ゼロ要素のインデックスを持つ`SmallBitSet`を返します。

[`SmallBitSet`](@ref)も参照してください。

# 例

```jldoctest
julia> v = FixedVector{4,Int8}([1, 0, 0, 3]);

julia> support(v)
SmallBitSet{UInt64} with 2 elements:
  1
  4
```
