```
poles(sys)
```

Compute the poles of system `sys`.

Note: Poles with multiplicity `n > 1` may suffer numerical inaccuracies on the order `eps(numeric_type(sys))^(1/n)`, i.e., a double pole in a system with `Float64` coefficients may be computed with an error of about `√(eps(Float64)) ≈ 1.5e-8`.

To compute the poles of a system with non-BLAS floats, such as `BigFloat`, install and load the package `GenericSchur.jl` before calling `poles`.
