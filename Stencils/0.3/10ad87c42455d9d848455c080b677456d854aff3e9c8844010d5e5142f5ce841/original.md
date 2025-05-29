```
Conditional <: Padding
```

Padding that doesn't change the array size, but checks `getindex` for out-of-bounds indexing, and inserts `padval` with [`Remove`](@ref) or values from the other side of the array with [`Wrap`](@ref).
