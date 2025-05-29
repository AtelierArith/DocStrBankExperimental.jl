```
MutableSmallSet{N,T} <: AbstractSmallSet{N,T}

MutableSmallSet{N,T}()
MutableSmallSet{N,T}(itr; unique = itr isa AbstractSet)
```

A set with element type `T` that can store up to `N` entries. The set is mutable and implements Julia's set interface.

If the element type is omitted, it will be inferred from the iterator, if possible. If `unique` is set to `true`, then the elements of `itr` are assumed to be distinct.

See also [`AbstractSmallSet`](@ref), [`SmallSet`](@ref).
