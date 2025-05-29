```
similar(M::MSet{T}) -> MSet{T}
similar(M::MSet, T::Type) -> MSet{T}
```

型 `T` の要素を持つ空の多重集合を作成します。

# 例

```jldoctest
julia> m = multiset([1,1,2,3,4,4,5])
MSet{Int64} with 7 elements:
  5
  4 : 2
  2
  3
  1 : 2

julia> similar(m)
MSet{Int64}()

julia> similar(m, QQFieldElem)
MSet{QQFieldElem}()
```
