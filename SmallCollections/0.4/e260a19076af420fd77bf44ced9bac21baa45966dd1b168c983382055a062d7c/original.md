```
SmallSet{N,T} <: AbstractSmallSet{N,T}

SmallSet{N,T}()
SmallSet{N,T}(itr; unique = itr isa AbstractSet)
```

An immutable set with element type `T` that can store up to `N` entries. All entries come from the iterator `itr` provided at construction time.

If the element type is omitted, it will be inferred from the iterator, if possible. If `unique` is set to `true`, then the elements of `itr` are assumed to be distinct.

See also [`AbstractSmallSet`](@ref), [`MutableSmallSet`](@ref).
