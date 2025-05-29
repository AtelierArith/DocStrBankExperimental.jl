```julia
addhopping!(tm::TBModel, R::AbstractVector{<:Integer}, hopping::Matrix{<:Number})
```

Add `hopping` to the Hamiltonian of `tm`.

`hopping` should be a `(tm.norbits, tm.norbits)` array containing the matrix ⟨0n|H|Rm⟩ with n and m indices. If R is [0, 0, 0], then `hopping` needs to be Hermitian.
