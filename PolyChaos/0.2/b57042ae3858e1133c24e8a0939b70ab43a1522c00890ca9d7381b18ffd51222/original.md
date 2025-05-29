```
lobatto(N::Int,α::AbstractVector{<:Real},β::AbstractVector{<:Real},endl::Real,endr::Real)
lobatto(α::AbstractVector{<:Real},β::AbstractVector{<:Real},endl::Real,endr::Real)
lobatto(N::Int,op::Union{OrthoPoly,AbstractCanonicalOrthoPoly},endl::Real,endr::Real)
lobatto(op::Union{OrthoPoly,AbstractCanonicalOrthoPoly},endl::Real,endr::Real)
```

Gauss-Lobatto quadrature rule. Given a weight function encoded by the recurrence coefficients for the associated orthogonal polynomials, the function generates the nodes and weights of the `(N+2)`-point Gauss-Lobatto quadrature rule for the weight function, having two prescribed nodes `endl`, `endr` (typically the left and right end points of the support interval, or points to the left resp. to the right thereof).

!!! note
    The function `radau` accepts at most `N = length(α) - 3` as an input, hence providing at most an `(length(α) - 1)`-point quadrature rule.


!!! note
    Reference: OPQ: A MATLAB SUITE OF PROGRAMS FOR GENERATING ORTHOGONAL POLYNOMIALS AND RELATED QUADRATURE RULES by Walter Gautschi

