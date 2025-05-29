```
sqrtmod(x::ZZRingElem, m::ZZRingElem)
```

Return a square root of $x (\mod m)$ if one exists. The remainder will be in the range $[0, m)$. We require that $m$ is prime, otherwise the algorithm may not terminate.

# Examples

```jldoctest
julia> sqrtmod(ZZ(12), ZZ(13))
5
```
