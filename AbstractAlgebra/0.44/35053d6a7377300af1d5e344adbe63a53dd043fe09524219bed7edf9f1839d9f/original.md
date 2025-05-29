```
is_skew_symmetric(M::MatrixElem)
```

Return `true` if the given matrix is skew symmetric with respect to its main diagonal, i.e., `transpose(M) == -M`, otherwise return `false`.

# Examples

```jldoctest
julia> M = matrix(ZZ, [0 -1 -2; 1 0 -3; 2 3 0])
[0   -1   -2]
[1    0   -3]
[2    3    0]

julia> is_skew_symmetric(M)
true

```
