```
lc, mvf = example_multiflow()
```

Create the Lefschetz complex and multivector field for the example from Figure 3 in the connection matrix paper by *Mrozek & Wanner*.

The function returns the Lefschetz complex `lc` over GF(2) and the multivector field `mvf`.

# Examples

```jldoctest
julia> lc, mvf = example_multiflow();

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0   0]
[0   0   0   0]
[0   0   0   0]
[0   0   0   0]

julia> print(cm.labels)
["BD", "DF", "AC", "CE"]
```
