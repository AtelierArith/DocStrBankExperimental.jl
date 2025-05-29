```
is_symmetric(a::MatrixElem{T}) where T <: RingElement
```

Return `true` if the given matrix is symmetric with respect to its main diagonal, i.e., `tr(M) == M`, otherwise return `false`.

Alias for `LinearAlgebra.issymmetric`.

# Examples

```jldoctest
julia> M = matrix(ZZ, [1 2 3; 2 4 5; 3 5 6])
[1   2   3]
[2   4   5]
[3   5   6]

julia> is_symmetric(M)
true

julia> N = matrix(ZZ, [1 2 3; 4 5 6; 7 8 9])
[1   2   3]
[4   5   6]
[7   8   9]

julia> is_symmetric(N)
false
```
