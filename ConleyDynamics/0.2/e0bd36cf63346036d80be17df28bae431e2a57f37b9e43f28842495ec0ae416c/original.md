```
lc, mvf = example_julia_logo()
```

Create the simplicial complex and multivector field for the example from Figure 1 in the connection matrix paper by *Mrozek & Wanner*.

The function returns the Lefschetz complex `lc` over GF(2) and the multivector field `mvf`.

# Examples

```jldoctest
julia> lc, mvf = example_julia_logo();

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0]
[0   0   1]
[0   0   0]

julia> print(cm.labels)
["D", "AC", "ABC"]
```
