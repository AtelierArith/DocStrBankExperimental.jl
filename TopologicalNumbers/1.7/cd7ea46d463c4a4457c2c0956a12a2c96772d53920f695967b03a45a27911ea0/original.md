```
T, L, P = skew_LTL(A::AbstractMatrix{T}; overwrite_a=false, calc_L=true, calc_P=true) where {T<:Number}
```

Bring a real or complex skew-symmetric matrix (A=-A^T) into tridiagonal form T (with zero diagonal) with a lower unit triangular matrix L such that P A P^T= L T L^T

A is overwritten if overwrite*a=true (default: false), L and P only calculated if calc*L=true or calc_P=true, respectively (default: true).
