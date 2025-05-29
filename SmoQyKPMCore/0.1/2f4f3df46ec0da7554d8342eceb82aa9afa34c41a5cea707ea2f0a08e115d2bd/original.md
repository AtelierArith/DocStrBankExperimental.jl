```
kpm_dot(
    A, kpm_expansion::KPMExpansion, U::T, V::T,
    tmp = zeros(eltype(V), size(V)..., 3)
) where {T<:AbstractVecOrMat}
```

If $U$ and $V$ are single vectors, then calculate the inner product

$$
\begin{align*}
S & = \langle U | F(A) | V \rangle \\
  & = \sum_{m=1}^M \langle U | c_m T_m(A^\prime) | V \rangle
\end{align*},
$$

where $A^\prime$ is the scaled version of $A$ using the `bounds`. If $U$ and $V$ are matrices, then calculate

$$
\begin{align*}
S & = \langle U | F(A) | V \rangle \\
  & = \frac{1}{N} \sum_{n=1}^N \sum_{m=1}^M \langle U_n | c_m T_m(A^\prime) | V_n \rangle
\end{align*},
$$

where $| U_n \rangle$ and $| V_n \rangle$ are the columns of each matrix.
