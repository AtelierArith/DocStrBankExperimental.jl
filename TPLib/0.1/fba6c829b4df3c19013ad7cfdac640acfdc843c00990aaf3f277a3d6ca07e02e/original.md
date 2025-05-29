```
compute_ext_rays_polar(M::Matrix{<:SemiRing}, n::Integer)
compute_ext_rays_polar(M::Matrix{<:Number}, n::Integer, semiring=:max)
```

Computes the set of the extreme rays of the polar of a tropical cone given by a generating set `M` in dimension `n`, see [3]. Each row of `M` contains `n` coefficients and represents a generator of the tropical cone. If the coefficients of `M` have type `MaxPlus{T}` or `MinPlus{T}`, then the computations are done in the max-plus or min-plus tropical semirings respectively. Otherwise, you can specify wether the coefficients should be converted to the semiring `:max` or `:min`. Returns a matrix `::Matrix{<:SemiRing}` in which every row is a tropical point generating the polar cone.

# References

[1] X. Allamigeon, S. Gaubert, and R. D. Katz. Tropical polar cones, hypergraph transversals, and mean payoff games. Linear Algebra Appl., 435(7):1549–1574, 2011. E-print arXiv:1004.2778.
