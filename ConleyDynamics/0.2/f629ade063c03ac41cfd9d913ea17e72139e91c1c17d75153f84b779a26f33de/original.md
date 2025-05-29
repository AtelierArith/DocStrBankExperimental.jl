```
lc, mvf, coords = example_forman2d()
```

Create the simplicial complex and multivector field for the example from Figure 3 in the FoCM 2020 paper by *Batko, Kaczynski, Mrozek, and Wanner*.

The function returns the Lefschetz complex `lc` over the finite field GF(2) and the multivector field `mvf`. If desired for plotting, the third return value `coords` gives a vector of coordinates for the vertices.

# Examples

```jldoctest
julia> lc, mvf = example_forman2d();

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0   0   1   0   1   0   0]
[0   0   0   0   0   1   0   0   0]
[0   0   0   0   1   1   1   0   0]
[0   0   0   0   0   0   0   0   1]
[0   0   0   0   0   0   0   1   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   1   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]

julia> print(cm.labels)
["D", "E", "F", "GJ", "BF", "EF", "HI", "ADE", "FGJ"]
```
