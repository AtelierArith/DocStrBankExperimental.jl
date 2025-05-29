```
multiset(T::Type) -> MSet{T}
```

Create an empty multi-set `M` with elements of type `T`.

# Examples

```jldoctest
julia> multiset(QQFieldElem)
MSet{QQFieldElem}()

julia> multiset()
MSet{Any}()
```
