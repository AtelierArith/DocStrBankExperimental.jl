```
QL <: Factorization
```

A QL matrix factorization stored in a packed format, typically obtained from [`ql`](@ref). If $A$ is an `m`×`n` matrix, then

$$
A = Q L
$$

where $Q$ is an orthogonal/unitary matrix and $L$ is lower triangular. The matrix $Q$ is stored as a sequence of Householder reflectors $v_i$ and coefficients $\tau_i$ where:

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

Iterating the decomposition produces the components `Q` and `L`.

The object has two fields:

  * `factors` is an `m`×`n` matrix.

      * The lower triangular part contains the elements of $L$, that is `L = tril(F.factors)` for a `QL` object `F`.
      * The superdiagonal part contains the reflectors $v_i$ stored in a packed format where $v_i$ is the $i$th column of the matrix `V = I + triu(F.factors, 1)`.
  * `τ` is a vector  of length `min(m,n)` containing the coefficients $au_i$.
