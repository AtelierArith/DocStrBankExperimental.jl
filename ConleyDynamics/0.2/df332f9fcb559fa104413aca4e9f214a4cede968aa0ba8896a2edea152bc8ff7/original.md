```
create_simplicial_complex(labels::Vector{String},
                          simplices::Vector{Vector{Int}};
                          p::Int=2)
```

Initialize a Lefschetz complex from a simplicial complex. The complex is over the rationals if `p=0`, and over `GF(p)` if `p>0`.

The vector `labels` contains a label for every vertex, while `simplices` contains all the highest-dimensional simplices necessary to define the simplicial complex. Every simplex is represented as a vector of `Int`, with entries corresponding to the vertex indices.

!!! warning
    Note that the labels all have to have the same character length!

