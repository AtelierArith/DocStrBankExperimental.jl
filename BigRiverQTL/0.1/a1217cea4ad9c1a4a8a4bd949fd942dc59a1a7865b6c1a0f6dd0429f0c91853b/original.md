```
select_marker(geno_selection::Geno, markers_selection:: Union{Vector{String}, InvertedIndex{Vector{String}}}) -> Geno
```

Select and return a subset of genetic markers from a `Geno` object based on specified marker names or their indices.

# Arguments

  * `geno_selection`: A `Geno` type or struct that contains genetic data.
  * `markers_selection`: A vector of marker names or an inverted index of marker names

```
to be selected from the `geno_selection`. The selection is applied to the marker names in the `Geno` object.
```

# Returns

  * `Geno`: A new `Geno` object that contains only the selected markers, their corresponding genetic information,

and the subset of the original genotypes related to these markers.
