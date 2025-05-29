```julia
    (1) distance(metric::Metric, P::ℍ{T}) where T<:RealOrComplex
    (2) distance(metric::Metric, P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
    (3) distance(metric::Metric, D::𝔻{S}) where S<:Real
    (4) distance(metric::Metric, D::𝔻{S}, E::𝔻{S}) where S<:Real
```

(1) Return $δ(P, I)$, the *distance* between positive definite matrix $P$ and the identity matrix.

(2) Return $δ(P, Q)$, the *distance* between positive definite matrices $P$ and $Q$.

(3) and (4) are specialized methods of (1) and (2), respectively, for real positive definite `Diagonal` matrices.

This is the square root of [`distanceSqr`](@ref) and is invoked with the same syntax therein.

**See also**: [`distanceMat`](@ref).
