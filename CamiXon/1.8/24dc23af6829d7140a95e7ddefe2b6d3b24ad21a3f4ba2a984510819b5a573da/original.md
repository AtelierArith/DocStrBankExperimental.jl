```
Gk(k::Int, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid) where T<:Real
```

$k^{th}$-order-multipole contribution to the *exchange* radial integral over  the (reduced) radial wavefunctions `P1` and 'P2' of two electrons in a central potential.

$$
F^{k}(nl;n^{\prime}l^{\prime})
=\int_{0}^{\infty}U_{F}^{k}(nl;\rho)\left[\tilde{R}_{n^{\prime}l^{\prime}}(\rho)\right]^{2}\rho^{2}d\rho.
$$
