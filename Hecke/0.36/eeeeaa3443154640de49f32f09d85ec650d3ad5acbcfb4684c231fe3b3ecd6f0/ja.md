```
multiplicity(s::MSet{T}, x::T) -> Int
```

マルチセット `s` における要素 `x` の重複度を返します。`x` が `s` に存在しない場合は 0 を返します。

# 例

```jldoctest
julia> m = multiset([1,1,2,3,4,4,5])
MSet{Int64} with 7 elements:
  5
  4 : 2
  2
  3
  1 : 2

julia> multiplicity(m, 2)
1

julia> multiplicity(m, 6)
0
```
