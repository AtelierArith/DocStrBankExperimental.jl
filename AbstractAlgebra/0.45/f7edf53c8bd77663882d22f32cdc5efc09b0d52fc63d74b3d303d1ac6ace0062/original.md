```
minors_iterator_with_position(A::MatElem, k::Int)
```

Return an iterator that computes the `k`-minors of `A` also specifying the row and column indices of the minor.

# Examples

```jldoctest
julia> A = ZZ[1 2 3; 4 5 6]
[1   2   3]
[4   5   6]

julia> first(minors_iterator_with_position(A, 2))
(-3, [1, 2], [1, 2])

```
