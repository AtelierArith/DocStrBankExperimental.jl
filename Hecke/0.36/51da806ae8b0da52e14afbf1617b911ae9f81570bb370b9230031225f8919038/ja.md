```
multiset(T::Type) -> MSet{T}
```

型 `T` の要素を持つ空の多重集合 `M` を作成します。

# 例

```jldoctest
julia> multiset(QQFieldElem)
MSet{QQFieldElem}()

julia> multiset()
MSet{Any}()
```
