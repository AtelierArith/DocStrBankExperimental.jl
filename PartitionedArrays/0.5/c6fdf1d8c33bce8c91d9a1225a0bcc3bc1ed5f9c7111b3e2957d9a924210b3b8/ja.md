```
scan(op,a;init,type)
```

`a`の値に対する演算`op`のスキャンを返します。`type=:inclusive`または`type=:exclusive`を使用して、包括的または排他的なスキャンを使用します。`init`は結果のすべての項目に加算されます。さらに、排他的スキャンの場合、結果の最初の項目は`init`に設定されます。

# 例

```jldoctest
julia> using PartitionedArrays

julia> a = [2,4,1,3]
4-element Vector{Int64}:
 2
 4
 1
 3

julia> scan(+,a,type=:inclusive,init=0)
4-element Vector{Int64}:
  2
  6
  7
 10

julia> scan(+,a,type=:exclusive,init=1)
4-element Vector{Int64}:
 1
 3
 7
 8
```
