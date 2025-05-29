```
radau(N::Int,α::AbstractVector{<:Real},β::AbstractVector{<:Real},end0::Real)
radau(α::AbstractVector{<:Real},β::AbstractVector{<:Real},end0::Real)
radau(N::Int,op::Union{OrthoPoly,AbstractCanonicalOrthoPoly},end0::Real)
radau(op::Union{OrthoPoly,AbstractCanonicalOrthoPoly},end0::Real)
```

Gauss-Radau quadrature rule. Given a weight function encoded by the recurrence coefficients `(α,β)`for the associated orthogonal polynomials, the function generates the nodes and weights `(N+1)`-point Gauss-Radau quadrature rule for the weight function having a prescribed node `end0` (typically at one of the end points of the support interval of w, or outside thereof).

!!! note
    The function `radau` accepts at most `N = length(α) - 2` as an input, hence providing at most an `(length(α) - 1)`-point quadrature rule.


!!! note
    Reference: OPQ: A MATLAB SUITE OF PROGRAMS FOR GENERATING ORTHOGONAL POLYNOMIALS AND RELATED QUADRATURE RULES by Walter Gautschi

