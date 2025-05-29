```
extract_multivectors(lc::LefschetzComplex, mvf::Vector{Vector{String}},
                     scells::Vector{String})
```

Extract all multivectors containing a provided selection of cells.

The function returns all multivectors which contain at least one of the cells in the input vector `scells`. The return argument has type `Vector{Vector{String}}`.
