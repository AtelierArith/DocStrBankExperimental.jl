```
 n_fermion(x::Real, β::Real) -> ::Float64
 n_fermion(x::Real, lsβ::AbstractVector{<:Real}) -> ::Vector{Float64}
  n_fermion(lsx::AbstractVector{<:Real}, β::Real) -> ::Vector{Float64}
```

The Fermi-Dirac distribution `x -> 1 / (e^{βx} + 1)`.
