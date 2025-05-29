```
kpm_moments!(
    μ::AbstractVector, A, kpm_expansion::KPMExpansion, U::T, V::T,
    tmp = zeros(eltype(V), size(V)..., 3)
) where {T<:AbstractVecOrMat}
```

If $U$ and $V$ are vector then calculate and return the first $M$ moments

$$
\mu_m = \langle U | T_m(A^\prime) | V \rangle,
$$

where $A^\prime$ is the rescaled version of $A$ using the `kpm_expansion.bounds`. If $U$ and $V$ are matrices then calculate the moments as

$$
\mu_m = \frac{1}{N} \sum_{n=1}^N \langle U_n | T_m(A^\prime) | V_n \rangle,
$$

where $| U_n \rangle$ and  $| V_n \rangle$ are are the n'th columns of each matrix.
