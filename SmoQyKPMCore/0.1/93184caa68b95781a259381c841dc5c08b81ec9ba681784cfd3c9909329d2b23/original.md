```
kpm_moments!(
    μ::AbstractVector, A, bounds, R::T,
    tmp = zeros(eltype(R), size(R)..., 3)
) where {T<:AbstractVecOrMat}
```

If $R$ is a vector, calculate and return the first $M$ moments as

$$
\mu_m = \langle R | T_m(A^\prime) | R \rangle
$$

where $A^\prime$ is the rescaled version of $A$ using the `bounds`. If $R$ is a matrix then calculate the moments as

$$
\mu_m = \frac{1}{N} \sum_{n=1}^N \langle R_n | T_m(A^\prime) | R_n \rangle,
$$

where $| R_n \rangle$ is the n'th column of $R$.
