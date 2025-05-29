```
minors(A::MatElem, k::Int)
```

Return an array consisting of the `k`-minors of `A`.

# Examples

```jldoctest
julia> A = ZZ[1 2 3; 4 5 6]
[1   2   3]
[4   5   6]

julia> minors(A, 2)
3-element Vector{BigInt}:
 -3
 -6
 -3

```
