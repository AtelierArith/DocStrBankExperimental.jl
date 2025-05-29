```
powers(a::Union{NCRingElement, MatElem}, d::Int)
```

Return an array $M$ of "powers" of `a` where $M[i + 1] = a^i$ for $i = 0..d$.

# Examples

```jldoctest
julia> M = ZZ[1 2 3; 2 3 4; 4 5 5]
[1   2   3]
[2   3   4]
[4   5   5]

julia> A = powers(M, 4)
5-element Vector{AbstractAlgebra.Generic.MatSpaceElem{BigInt}}:
 [1 0 0; 0 1 0; 0 0 1]
 [1 2 3; 2 3 4; 4 5 5]
 [17 23 26; 24 33 38; 34 48 57]
 [167 233 273; 242 337 394; 358 497 579]
 [1725 2398 2798; 2492 3465 4044; 3668 5102 5957]

```
