```
legendre!(norm::AbstractLegendreNorm, Λ, l::Integer, m::Integer, x)
```

Fills the array `Λ` with the Legendre polynomial values $N_ℓ^m P_ℓ^m(x)$ up to/of degree(s) `l` and order(s) `m` for the normalization scheme `norm`. `Λ` must be an array with between 0 and 2 more dimensions than `x`, with the leading dimensions having the same shape as `x`.

  * If `ndims(Λ) == ndims(x)`, then `Λ` is filled with the polynomial values at `x` for degree `l` and order `m`.
  * If `ndims(Λ) == ndims(x) + 1`, then `l` is interpreted as `lmax`, and `Λ` filled with polynomial values for all degrees `0 ≤ l ≤ lmax` of order `m`.
  * If `ndims(Λ) == ndims(x) + 2`, then `l` is interpreted as `lmax` and `m` as `mmax`, and `Λ` is filled with polynomial values for all degrees `0 ≤ l ≤ lmax` and orders `0 ≤ m ≤ min(mmax, l)`.
