```
wignerD(j, α::Real, β::Real, γ::Real, [Jy = zeros(ComplexF64, 2j+1, 2j+1)])
```

Evaluate the Wigner D-matrix with elements $D^j_{m,n}(α,β,γ)$ for the angular momentum $j$ and the Euler angles $α$, $β$ and $γ$. The momentum $j$ may be an integer or a half-integer, and must be non-negative. Optionally the pre-allocated matrix `Jy` may be provided, which must be a `ComplexF64` matrix of size `(2j+1, 2j+1)`, and may be overwritten during the calculation.
