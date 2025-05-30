```
collect(collection)
```

コレクションまたはイテレータ内のすべてのアイテムの `Array` を返します。辞書の場合、`Vector{Pair{KeyType, ValType}}` を返します。引数が配列のようであるか、[`HasShape`](@ref IteratorSize) 特性を持つイテレータである場合、結果は引数と同じ形状および次元数になります。

生成器を `Array` に変換するために、内包表記によって使用されます。

# 例

```jldoctest
julia> collect(1:2:13)
7-element Vector{Int64}:
  1
  3
  5
  7
  9
 11
 13

julia> [x^2 for x in 1:8 if isodd(x)]
4-element Vector{Int64}:
  1
  9
 25
 49
```
