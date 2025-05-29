```
lc, mvf = example_subdivision(mvftype)
```

Create the Lefschetz complex and multivector field for the example from Figure 11 in the connection matrix paper by *Mrozek & Wanner*.

Depending on the value of `mvftype`, return the multivector (0=default) or one of the two combinatorial vector field (1,2) examples.

The function returns the Lefschetz complex `lc` over the rationals and the multivector field `mvf`.

# Examples

```jldoctest
julia> lc, mvf = example_subdivision(1);

julia> cm = connection_matrix(lc, mvf);

julia> full_from_sparse(cm.matrix)
5×5 Matrix{Rational{Int64}}:
 0  0  -1  -1  -1
 0  0   1   0   0
 0  0   0   0   0
 0  0   0   0   0
 0  0   0   0   0
```
