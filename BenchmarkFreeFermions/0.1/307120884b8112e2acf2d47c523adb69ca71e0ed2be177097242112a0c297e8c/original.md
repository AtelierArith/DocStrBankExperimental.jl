```
 GreenFunction(ξ::Vector{Float64}, V::Matrix{F}, β::Real; τ::Number=0.0) -> G::Matrix{F}
 GreenFunction(ξ::Vector{Float64}, V::Matrix{F}, β::Real,
 i::Int64, j::Int64;
 τ::Number=0.0,
 reverse::Bool = false) -> Gij::F
```

Compute the Green's funtion `Gij(τ) = ⟨c_i(τ) c_j^dag⟩` (up to a coefficient) with the shifted single particle spectrum `ξ = ϵ - μ` and the eigenvectors `V` obtained from `Tij = - V diagm(ϵ) V'`.

# Kwargs

```
 reverse::Bool = false
```

Return `⟨c_i^dag(τ) c_j⟩` instead if `reverse = true`.
