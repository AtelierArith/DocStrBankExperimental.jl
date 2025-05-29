```
integrateK(Ak, Q::QDHT; dim=1)
```

Radial integral of `A`, over the aperture of `Q` in reciprocal space.

Assuming `A` contains samples of a function `f(k)` at sample points `Q.k`, then `integrateR(A, Q)` approximates ∫f(k)k dk from k=0 to k=∞.

!!! note
    `integrateR` and `integrateK` fulfill Parseval's theorem, i.e. for some array `A`, `integrateR(abs2.(A), q)` and `integrateK(abs2.(q*A), q)` are equal, **but** `integrateR(A, q)` and `integrateK(q*A, q)` are **not** equal.


# Examples

```jldoctest
julia> q = QDHT{0, 1}(10, 128); A = exp.(-q.r.^2/2);
julia> integrateR(abs2.(A), q) ≈ 0.5 # analytical solution of ∫exp(-r²)r dr from 0 to ∞
true
julia> Ak = q*A;
julia> integrateK(abs2.(Ak), q) ≈ 0.5 # Same result
true

```
