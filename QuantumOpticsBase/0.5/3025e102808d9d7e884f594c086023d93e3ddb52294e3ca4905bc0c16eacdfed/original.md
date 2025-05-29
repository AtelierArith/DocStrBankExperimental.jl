```
displace_analytical(b::FockBasis, alpha::Number)
displace_analytical(::Type{T}, b::FockBasis, alpha::Number)
```

Get the "analytical" displacement operator, whose matrix elements match (up to numerical imprecision) those of the exact infinite-dimensional displacement operator. This is different to the result of `displace(..., alpha)`, which computes the matrix exponential `exp(alpha * a' - conj(alpha) * a)` using finite-dimensional (truncated) creation and annihilation operators `a'` and `a`.
