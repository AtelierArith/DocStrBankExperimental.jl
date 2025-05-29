```
function bosonize(opstr::OpString{T1},
                  sites::Vector{Index{T2}}) where {T1 <: Number, T2}
```

Returns an `OpString` after "bosonizing" the original with Jordan-Wigner strings as needed. See [`bosonize`](@ref).
