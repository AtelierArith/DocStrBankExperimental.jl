```
max_fields(f::MPoly{T}) where {T <: RingElement}
```

Return a tuple `(degs, biggest)` consisting of an array `degs` of the maximum exponent for each field in the exponent vectors of `f` and an integer which is the largest of the entries in `degs`. The array `degs` will have `n + 1` entries in the case of a degree ordering, or `n` otherwise, where `n` is the number of variables of the polynomial ring `f` belongs to. The fields are returned in the order they exist in the internal representation (which is not intended to be specified, and not needed for current applications).
