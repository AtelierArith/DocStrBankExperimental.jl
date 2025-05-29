```
pfaffian_householder(A::AbstractMatrix{T}; overwrite_a=false) where {T<:Real}
```

Compute the Pfaffian of a real or complex skew-symmetric matrix A (A=-A^T). If overwrite_a=true, the matrix A is overwritten in the process. This function uses the Householder tridiagonalization.

Note that the function pfaffian*schur() can also be used in the real case. That function does not make use of the skew-symmetry and is only slightly slower than pfaffian*householder().
