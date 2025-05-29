```
wignerd!(d, j, β::Real, [Jy = zeros(ComplexF64, 2j+1, 2j+1)])
```

Evaluate the Wigner d-matrix with elements $d^j_{m,n}(β)$ for the angular momentum $j$ and the rotation angle $β$, and store the result in `d`. The momentum $j$ may be an integer or a half-integer, and must be non-negative. Optionally the pre-allocated matrix `Jy` may be provided, which must be a `ComplexF64` matrix of size `(2j+1, 2j+1)`, and may be overwritten during the calculation.
