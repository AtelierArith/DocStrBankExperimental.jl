```julia
getA(tm::AbstractTBModel, α::Int64, k::AbstractVector{<:Real})
-->A::Matrix{ComplexF64}
```

Calculate Berry connection $i⟨u_n|∂_α|u_m⟩$ for `tm` at `k`.

Calculation method is provided in [Wang et al, 2019]. The relevant equation is Eq. (14). Since Eq. (14) assumes band m is nondegenerate, A[n, m] is only correct if m is nondegenerate or completely degenerate.
