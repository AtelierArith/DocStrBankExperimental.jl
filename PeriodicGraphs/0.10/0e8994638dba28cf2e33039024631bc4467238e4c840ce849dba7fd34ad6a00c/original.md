```
RingAttributions{D} <: AbstractVector{RingIncluding{D}}
```

Represent a set of rings of a `PeriodicGraph{D}`.

For `ra` of type `RingAttributions{D}`, `ra[i]` is a [`RingIncluding{D}`](@ref) object representing the set of rings including `PeriodicVertex{D}(i)`.
