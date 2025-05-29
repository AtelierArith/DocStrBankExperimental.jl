```
Fk(k::Int, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid) where T<:Real
```

$k^{th}$-order-multipole contribution to the *direct* radial integral over  the (reduced) radial wavefunctions `P1` and `P2` of two electrons (in the orbitals  $nl$ and $n^{\prime}l^{\prime}$) in a central potential field.

$$
F^{k}(nl;n^{\prime}l^{\prime})
=\int_{0}^{\infty}U_{F}^{k}(nl;\rho)\left[\tilde{R}_{n^{\prime}l^{\prime}}(\rho)\right]^{2}\rho^{2}d\rho
=\int_{0}^{\infty}U_{F}^{k}(n^{\prime}l^{\prime};\rho)\left[\tilde{R}_{nl}(\rho)\right]^{2}\rho^{2}d\rho.
$$

```
Fk(k::Int, P::Vector{T}, grid::CamiDiff.Grid) where T<:Real
```

$k^{th}$-order contribution to the *direct* radial integral over the (reduced)  radial wavefunction `P` of two *equivalent* $nl$ electrons in a central potential.

$$
F^{k}(nl)
=\int_{0}^{\infty}U_{F}^{k}(nl;\rho)\left[\tilde{R}_{nl}(\rho)\right]^{2}\rho^{2}d\rho.
$$
