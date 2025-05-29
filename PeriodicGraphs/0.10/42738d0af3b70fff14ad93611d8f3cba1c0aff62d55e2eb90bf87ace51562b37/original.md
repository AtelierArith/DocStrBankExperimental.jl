```
RingIncluding{D} <: AbstractVector{OffsetVertexIterator{D}}
```

The list of rings of a `PeriodicGraph{D}` including a particular vertex `PeriodicVertex{D}(i)`.

The object is iterable and indexable by an integer: for `ri` of type `RingIncluding{D}`, `ri[j]` is an iterable over the vertices of the `j`-th ring including vertex `i`.
