```
kpm_dot(
    A, kpm_expansion::KPMExpansion, R::T,
    tmp = zeros(eltype(R), size(R)..., 3)
) where {T<:AbstractVecOrMat}
```

If $R$ is a single vector, then calculate the inner product

$$
\begin{align*}
S & = \langle R | F(A) | R \rangle \\
  & = \sum_{m=1}^M \langle R | c_m T_m(A^\prime) | R \rangle
\end{align*},
$$

where $A^\prime$ is the scaled version of $A$ using the `bounds`. If $R$ is a matrix, then calculate

$$
\begin{align*}
S & = \langle R | F(A) | R \rangle \\
  & = \frac{1}{N} \sum_{n=1}^N \sum_{m=1}^M \langle R_n | c_m T_m(A^\prime) | R_n \rangle
\end{align*},
$$

where $| R_n \rangle$ is a column of $R$.
