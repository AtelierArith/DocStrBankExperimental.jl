```
T, Q = skew_tridiagonalize(A::AbstractMatrix{T}; overwrite_a=false, calc_q=true) where {T<:Number}
```

or

```
T = skew_tridiagonalize(A::AbstractMatrix{T}; overwrite_a=false, calc_q=false) where {T<:Number}
```

Bring a real or complex skew-symmetric matrix (A=-A^T) into tridiagonal form T (with zero diagonal) with a orthogonal (real case) or unitary (complex case) matrix U such that A = Q T Q^T (Note that Q^T and *not* Q^dagger also in the complex case)

A is overwritten if overwrite*a=true (default: false), and Q only calculated if calc*q=true (default: true)
