```
signature(f::ZZPolyRingElem)
```

Return the signature of $f$, i.e. a tuple $(r, s)$ such that $r$ is the number of real roots of $f$ and $s$ is half the number of complex roots.

# Examples

```jldoctest
julia> R, x = polynomial_ring(ZZ, "x");

julia> signature(x^3 + 3x + 1)
(1, 1)
```
