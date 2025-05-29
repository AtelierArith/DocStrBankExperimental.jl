```
vec(px)
```

Convert a `BilateralParcellation` from its internal `Dict`-based representation into  a `Vector{T}`. `T` must have a `zeros(T, ...)` method. Warning: this is not a sensible representation in the event that any `Parcel`s overlap.
