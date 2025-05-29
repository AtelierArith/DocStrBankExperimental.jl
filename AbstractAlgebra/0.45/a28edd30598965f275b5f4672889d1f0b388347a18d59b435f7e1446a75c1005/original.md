```
minors_with_position(A::MatElem, k::Int)
```

Return an array consisting of the `k`-minors of `A` and the respective data on the rows and columns involved.

# Examples

```jldoctest
julia> A = ZZ[1 2 3; 4 5 6]
[1   2   3]
[4   5   6]

julia> minors_with_position(A, 2)
3-element Vector{Tuple{BigInt, Vector{Int64}, Vector{Int64}}}:
 (-3, [1, 2], [1, 2])
 (-6, [1, 2], [1, 3])
 (-3, [1, 2], [2, 3])

```
