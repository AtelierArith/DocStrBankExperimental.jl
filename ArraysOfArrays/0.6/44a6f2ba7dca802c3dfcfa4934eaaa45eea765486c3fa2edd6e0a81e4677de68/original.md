```
flatview(A::VectorOfArrays{T})::Vector{T}
```

Returns the internal serialized representation of all element arrays of `A` as a single vector. Do *not* change the length of the returned vector, as it would break the inner consistency of `A`.
