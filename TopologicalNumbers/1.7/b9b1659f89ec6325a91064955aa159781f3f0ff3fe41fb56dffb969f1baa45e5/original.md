```
pfaffian(A::AbstractMatrix{T}, overwrite_a=false, method='P') where {T<:Number}
```

Compute the Pfaffian of a real or complex skew-symmetric matrix A (A=-A^T). If overwrite_a=true, the matrix A is overwritten in the process. This function uses either the Parlett-Reid algorithm (method='P', default), or the Householder tridiagonalization (method='H')
