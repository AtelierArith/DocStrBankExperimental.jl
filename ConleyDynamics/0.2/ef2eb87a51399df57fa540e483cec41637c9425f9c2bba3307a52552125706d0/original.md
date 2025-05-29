```
lc1, lc2, mvf = example_small_periodicity()
```

Create two representations of the Lefschetz complex and the multivector field for the example from Figure 4 in the connection matrix paper by *Mrozek & Wanner*.

The complexes `lc1` and `lc2` are just two representations of the same complex, but they lead to different connection matrices. Both Lefschetz complexes are defined over the finite field GF(2).

The function returns the Lefschetz complexes `lc1` and `lc2`, as well as the multivector field `mvf`.

# Examples

```jldoctest
julia> lc1, lc2, mvf = example_small_periodicity();

julia> cm1 = connection_matrix(lc1, mvf);

julia> cm2 = connection_matrix(lc2, mvf);

julia> full_from_sparse(cm1.matrix)
4×4 Matrix{Int64}:
 0  0  0  0
 0  0  0  1
 0  0  0  1
 0  0  0  0

julia> print(cm1.labels)
["A", "a", "b", "alpha"]

julia> full_from_sparse(cm2.matrix)
4×4 Matrix{Int64}:
 0  0  0  0
 0  0  0  0
 0  0  0  1
 0  0  0  0

julia> print(cm2.labels)
["A", "c", "b", "alpha"]
```
