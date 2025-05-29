```julia
getdH(tm::AbstractTBModel, order::Tuple{Int64,Int64,Int64},
    k::AbstractVector{<:Real})::Matrix{ComplexF64}
```

Calculate `order` derivative of Hamiltonian.
