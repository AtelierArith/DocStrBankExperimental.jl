```
exchange(s::S, i::Integer, j::Integer) where S <: SmallBitSet -> S
```

要素 `i` が存在する場合は `j` に置き換え、逆も同様にしてセット `s` を返します。もし `i` が `j` と等しい場合、セットは変更されません。

この関数は、同等の `replace(s, i => j, j => i)` よりも高速です。

詳細は `Base.replace` を参照してください。

# 例

```jldoctest
julia> s = SmallBitSet((1, 2)); exchange(s, 1, 2)
SmallBitSet{UInt64} with 2 elements:
  1
  2

julia> s = SmallBitSet((1, 2)); exchange(s, 2, 3)
SmallBitSet{UInt64} with 2 elements:
  1
  3

julia> s = SmallBitSet((1, 2)); exchange(s, 3, 4)
SmallBitSet{UInt64} with 2 elements:
  1
  2

julia> s = SmallBitSet((1, 2)); exchange(s, 1, 1)
SmallBitSet{UInt64} with 2 elements:
  1
  2
```
