```
mutable struct MomentMatrix{T, B<:MultivariateBases.AbstractPolynomialBasis, MT<:AbstractMatrix{T}} <: AbstractMeasureLike{T}
    Q::MT
    basis::B
    support::Union{Nothing, AlgebraicSet}
end
```

Measure $\nu$ represented by the moments of the monomial matrix $x x^\top$ in the symmetric matrix `Q`. The set of points that are zeros of all the polynomials $p$ such that $\mathbb{E}_{\nu}[p] = 0$ is stored in the field `support` when it is computed.
