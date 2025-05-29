```
LDR{T<:Number, E<:Real} <: Factorization{T}
```

Represents the matrix factorization $A = L D R$ for a square matrix $A$, where $L$ is a unitary matrix, $D$ is a diagonal matrix of strictly positive real numbers, and $R$ is defined such that $|\det R| = 1$.

This factorization is based on a column-pivoted QR decomposition $A P = Q R',$ such that

$$
\begin{align*}
L &:= Q \\
D &:= \vert \textrm{diag}(R') \vert \\
R &:= \vert \textrm{diag}(R') \vert^{-1} R' P^T\\
\end{align*}
$$

# Fields

  * `L::Matrix{T}`: The left unitary matrix $L$ in a [`LDR`](@ref) factorization.
  * `d::Vector{E}`: A vector representing the diagonal matrix $D$ in a [`LDR`](@ref) facotorization.
  * `R::Matrix{T}`: The right matrix $R$ in a [`LDR`](@ref) factorization.
