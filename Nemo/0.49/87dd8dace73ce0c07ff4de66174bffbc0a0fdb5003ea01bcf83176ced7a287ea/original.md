```
lift(::ZZRing, x::FqFieldElem) -> ZZRingElem
```

Given an element $x$ of a prime field $\mathbf{F}_p$, return a preimage under the canonical map $\mathbf{Z} \to \mathbf{F}_p$.

# Examples

```jldoctest
julia> K = GF(19);

julia> lift(ZZ, K(3))
3
```
