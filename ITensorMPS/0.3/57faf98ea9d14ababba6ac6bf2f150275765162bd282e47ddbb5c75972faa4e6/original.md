```
logdot(B::MPO, y::MPS, A::MPO, x::MPS)
Compute the logarithm of the inner product `⟨y|A|x⟩` efficiently and exactly.
This is useful for larger MPS/MPO, where in the limit of large numbers of sites the inner product can diverge or approach zero.
Same as [`loginner`](@ref).
```
