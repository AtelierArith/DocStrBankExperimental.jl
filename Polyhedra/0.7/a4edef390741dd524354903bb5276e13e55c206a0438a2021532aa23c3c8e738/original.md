```
volume(p::Polyhedron{T}) where {T}
```

Returns the `fulldim(p)`-dimensional hyper-volume of the polyhedron `p`. Returns `Inf` or `-one(T)` if it is infinite depending on whether the type `T` has an infinite value.
