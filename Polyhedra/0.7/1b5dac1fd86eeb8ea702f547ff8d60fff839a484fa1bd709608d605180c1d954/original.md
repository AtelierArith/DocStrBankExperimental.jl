```
surface(p::Polyhedron{T}) where {T}
```

Returns the `fulldim(p)-1`-dimensional hyper-volume of the surface of the polyhedron `p`. Returns `Inf` or `-one(T)` if it is infinite depending on whether the type `T` has an infinite value.
