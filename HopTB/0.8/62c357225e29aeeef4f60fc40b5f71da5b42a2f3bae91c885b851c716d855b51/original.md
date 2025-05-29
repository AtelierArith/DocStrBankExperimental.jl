```julia
function getdr(tm::AbstractTBModel, α::Int64, β::Int64, k::AbstractVector{<:Real})
-->dr::Matrix{ComplexF64}
```

Compute $∂_β r_α$ for `tm` at `k`. r[n, m] = A[n, m] if n != m and r[n, n] = 0.

dr is calculated by directly differentiating Eq. (14) of [Wang et al, 2019]. dr[n, m] is only correct when (i) both band n and band m are nondegenerate or (ii) both band n and band m are completely degenerate but $E_n≠E_m$.
