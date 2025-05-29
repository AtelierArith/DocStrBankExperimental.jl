```
RQ <: Factorization
```

An RQ matrix factorization stored in a packed format, typically obtained from [`rq`](@ref). If $A$ is an `m`×`n` matrix, then

$$
A = [0 R] Q
$$

where $Q$ is an orthogonal/unitary matrix and $R$ is upper triangular (trapezoidal if `m < n`). The matrix $Q$ is stored as a sequence of Householder reflectors $v_i$ and coefficients $\tau_i$ where:

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

Iterating the decomposition produces the components `R` and `Q`.

The object has two fields:

  * `factors` is an `m`×`n` matrix.

      * The upper triangular part contains the elements of $R$, that is `R = triu(F.factors)` for a `QR` object `F`.
      * The subdiagonal part contains the reflectors $v_i$ stored in a packed format where $v_i$ is the $i$th column of the matrix `V = I + tril(F.factors, -1)`.
  * `τ` is a vector  of length `min(m,n)` containing the coefficients $au_i$.
