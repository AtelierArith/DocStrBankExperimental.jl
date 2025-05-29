```
gauss(N::Int,α::AbstractVector{<:Real},β::AbstractVector{<:Real})
gauss(α::AbstractVector{<:Real},β::AbstractVector{<:Real})
gauss(N::Int,op::Union{OrthoPoly,AbstractCanonicalOrthoPoly})
gauss(op::Union{OrthoPoly,AbstractCanonicalOrthoPoly})
```

Gauss quadrature rule, also known as Golub-Welsch algorithm

`gauss()` generates the `N` Gauss quadrature nodes and weights for a given weight function. The weight function is represented by the `N` recurrence coefficients for the monic polynomials orthogonal with respect to the weight function.

!!! note
    The function `gauss` accepts at most `N = length(α) - 1` quadrature points, hence providing at most an `(length(α) - 1)`-point quadrature rule.


!!! note
    If no `N` is provided, then `N = length(α) - 1`.

