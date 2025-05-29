```
create_simplicial_complex(labels::Vector{String},
                          simplices::Vector{Vector{String}};
                          p::Int=2)
```

Initialize a Lefschetz complex from a simplicial complex. The complex is over the rationals if `p=0`, and over `GF(p)` if `p>0`.

The vector `labels` contains a label for every vertex, while `simplices` contains all the highest-dimensional simplices necessary to define the simplicial complex.
