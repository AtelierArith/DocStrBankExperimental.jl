```
r_scale(c::Real,β::AbstractVector{<:Real},α::AbstractVector{<:Real})
```

Given the recursion coefficients `(α,β)` for a system of orthogonal polynomials that are orthogonal with respect to some positive weight $m(t)$, this function returns the recursion coefficients `(α_,β_)` for the scaled measure $c m(t)$ for some positive $c$.
