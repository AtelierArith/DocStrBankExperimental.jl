```
function bosonize(os::OpStrings{T1}, sites::Vector{Index{T2}}) where {T1 <: Number, T2}
```

Returns an `OpStrings` after "bosonizing" the original with Jordan-Wigner strings as needed. See [`bosonize`](@ref).
