```
integer_lattice([B::MatElem]; gram) -> ZZLat
```

Return the Z-lattice with basis matrix $B$ inside the quadratic space with Gram matrix `gram`.

If the keyword `gram` is not specified, the Gram matrix is the identity matrix. If $B$ is not specified, the basis matrix is the identity matrix.

# Examples

```jldoctest
julia> L = integer_lattice(matrix(QQ, 2, 2, [1//2, 0, 0, 2]));

julia> gram_matrix(L) == matrix(QQ, 2, 2, [1//4, 0, 0, 4])
true

julia> L = integer_lattice(gram = matrix(ZZ, [2 -1; -1 2]));

julia> gram_matrix(L) == matrix(ZZ, [2 -1; -1 2])
true
```
