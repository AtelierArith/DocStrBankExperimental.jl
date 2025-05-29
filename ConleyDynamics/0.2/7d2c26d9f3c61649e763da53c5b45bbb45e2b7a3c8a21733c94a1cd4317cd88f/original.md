```
lc1, lc2, mvf, coords1, coords2 = example_nonunique()
```

Create two representations of a simplicial complex and one multivector field which illustrates nonunique connection matrices.

The two complexes `lc1` and `lc2` represent the same simplicial complex over GF(2), but differ in the ordering of the labels.

The function returns the Lefschetz complexes `lc1` and `lc2`, as well as the multivector field `mvf`. If desired for plotting, the fourth and fifth return values `coords1` and `coords2` give vectors of coordinates for the vertices of the two complexes.

# Examples

```jldoctest
julia> lc1, lc2, mvf = example_nonunique();

julia> cm1 = connection_matrix(lc1, mvf);

julia> cm2 = connection_matrix(lc2, mvf);

julia> sparse_show(cm1.matrix)
[0   0   0   1   0   1   0   0   0]
[0   0   0   1   0   1   0   0   0]
[0   0   0   0   0   0   0   1   1]
[0   0   0   0   0   0   1   1   0]
[0   0   0   0   0   0   0   1   0]
[0   0   0   0   0   0   1   1   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]

julia> print(cm1.labels)
["2", "7", "79", "29", "45", "67", "168", "349", "789"]
julia> sparse_show(cm2.matrix)
[0   0   0   1   0   1   0   0   0]
[0   0   0   1   0   1   0   0   0]
[0   0   0   0   0   0   1   0   1]
[0   0   0   0   0   0   1   1   0]
[0   0   0   0   0   0   0   1   0]
[0   0   0   0   0   0   1   1   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]

julia> print(cm2.labels)
["2", "8", "78", "29", "45", "67", "168", "349", "789"]
```
