```
integrateR(A, Q::QDHT; dim=1)
```

Radial integral of `A`, over the aperture of `Q` in real space.

Assuming `A` contains samples of a function `f(r)` at sample points `Q.r`, then `integrateR(A, Q)` approximates ∫f(r)r dr from r=0 to r=∞.

!!! note
    `integrateR` and `integrateK` fulfill Parseval's theorem, i.e. for some array `A`, `integrateR(abs2.(A), q)` and `integrateK(abs2.(q*A), q)` are equal, **but** `integrateR(A, q)` and `integrateK(q*A, q)` are **not** equal.


!!! warning
    using `integrateR` to integrate a function (i.e. `A` rather than `abs2(A)`) is only supported for the 0th-order QDHT. For more details see [Derivations](@ref).


# Examples

```jldoctest
julia> q = QDHT{0, 1}(10, 128); A = exp.(-q.r.^2/2);
julia> integrateR(abs2.(A), q) ≈ 0.5 # analytical solution of ∫exp(-r²)r dr from 0 to ∞
true
```
