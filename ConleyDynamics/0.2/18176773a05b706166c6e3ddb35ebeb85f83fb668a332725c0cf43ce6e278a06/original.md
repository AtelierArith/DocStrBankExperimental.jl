```
lc, mvf, coords = example_three_cm(mvftype)
```

Create the simplicial complex and multivector field for the example from Figure 2 in the connection matrix paper by *Mrozek & Wanner*.

Depending on the value of `mvftype`, return the periodic orbit (0=default) or one of the three gradient (1,2,3) examples.

The function returns the Lefschetz complex `lc` over the rational field and the multivector field `mvf`. If desired for plotting, the third return value `coords` gives a vector of coordinates for the vertices.

# Examples

```jldoctest
julia> lc, mvf = example_three_cm(0);

julia> cm = connection_matrix(lc, mvf);

julia> print(cm.labels)
["A", "C", "CE", "AC", "BD", "DF", "ABC", "EFG"]

julia> full_from_sparse(cm.matrix)
8×8 Matrix{Rational{Int64}}:
 0  0  0  -1  -1  0   0  0
 0  0  0   1   1  0   0  0
 0  0  0   0   0  0   0  0
 0  0  0   0   0  0  -1  0
 0  0  0   0   0  0   1  0
 0  0  0   0   0  0   0  1
 0  0  0   0   0  0   0  0
 0  0  0   0   0  0   0  0
```
