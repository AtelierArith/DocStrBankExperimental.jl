```
rm_hermite(N::Int,mu::Real)
rm_hermite(N::Int)
```

Creates `N` recurrence coefficients for monic generalized Hermite polynomials that are orthogonal on $(-\infty,\infty)$ relative to $w(t) = |t|^{2 \mu} \mathrm{e}^{-t^2}$

The call `rm_hermite(N)` is the same as `rm_hermite(N,0)`.
