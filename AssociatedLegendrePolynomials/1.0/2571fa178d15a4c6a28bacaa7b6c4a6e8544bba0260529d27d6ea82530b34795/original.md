```
p = legendre(norm::AbstractLegendreNorm, l::DimOrInd, m::DimOrInd, x)
```

Computes the associated Legendre polynomials $N_ℓ^m P_ℓ^m(x)$ of degree(s) `l` and order(s) `m` at `x` for the normalization scheme `norm`.

  * If `l` and `m` are integers, returns a single value.
  * If `l` is a range `0:lmax` and `m` an integer, returns the vector of values for order `m` and all degrees `0 ≤ l ≤ lmax`.
  * If `l` is a range `0:lmax` and `m` is a range `0:mmax`, returns the matrix of values for all degrees `0 ≤ l ≤ lmax` and orders `0 ≤ m ≤ mmax`.

Note that in both the second and third cases, the ranges must have a first index of 0.
