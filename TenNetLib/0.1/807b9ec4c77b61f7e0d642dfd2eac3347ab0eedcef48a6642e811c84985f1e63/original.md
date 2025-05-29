```
function removeIdsZeros(os::OpStrings{T}) where {T <: Number}
```

Returns an `OpStrings` with all "Id" operators removed from the original, as well as any `OpString` term that has `coeff` less than `Float64_threshold()`.
