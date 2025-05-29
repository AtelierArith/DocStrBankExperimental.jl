```
select_sample(geno_selection::Geno, markers_selection:: Union{Vector{String}, InvertedIndex{Vector{String}}}) -> Geno
```

Select and return a subset of genetic samples from a `Geno` object based on specified samples names or their indices.

# Arguments

  * `geno_selection`: A `Geno` type or struct that contains genetic data.
  * `samples_selection`: A vector of samples names or an inverted index of samples names

```
to be selected from the `geno_selection`. The selection is applied to the samples names in the `Geno` object.
```

# Returns

  * `Geno`: A new `Geno` object that contains only the selected samples, their corresponding genetic information,

and the subset of the original genotypes related to these samples. ___
