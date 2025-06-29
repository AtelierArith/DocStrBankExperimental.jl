```
getyamanishi(db)
```

Get a tuple of matrices corresponding to the drug-target adjacency matrix and drug-drug similarity matrix for a given Yamanishi (2008) dataset.

# Arguments

  * `db`: Dataset ID (any of the following: "nr", "ic", "gpcr" or "e")

# Example

```jldoctest
julia> dt, dd = getyamanishi("nr");

julia> dt[1:5, 1:5]
5×5 Named Matrix{Float64}
 A ╲ B │  hsa190  hsa2099  hsa2100  hsa2101  hsa2103
───────┼────────────────────────────────────────────
D00040 │     0.0      0.0      0.0      0.0      0.0
D00066 │     0.0      1.0      0.0      0.0      0.0
D00067 │     0.0      1.0      0.0      0.0      0.0
D00075 │     0.0      0.0      0.0      0.0      0.0
D00088 │     0.0      0.0      0.0      0.0      0.0

julia> dd[1:5, 1:5]
5×5 Named Matrix{Float64}
 A ╲ B │   D00040    D00066    D00067    D00075    D00088
───────┼─────────────────────────────────────────────────
D00040 │      1.0  0.545455  0.297297   0.53125  0.459459
D00066 │ 0.545455       1.0  0.387097  0.833333  0.689655
D00067 │ 0.297297  0.387097       1.0  0.464286  0.352941
D00075 │  0.53125  0.833333  0.464286       1.0  0.678571
D00088 │ 0.459459  0.689655  0.352941  0.678571       1.0
```

# Extended help

The provided Yamanishi (2008) [1] datasets (ID) are:

  * 'Nuclear Receptor' (nr)
  * 'Ion Channels' (ic)
  * 'GPCR' (gpcr)
  * 'Enzyme' (e)

This function returns 2 distinct adjacency matrices:

  * Binary drug-target interaction matrix, obtained from biological annotations
  * Continuous drug-drug similarity matrix, obtained from SIMCOMP

# References

1. Yamanishi, Y., Araki, M., Gutteridge, A., Honda, W., & Kanehisa, M. (2008). Prediction of drug–target interaction networks from the integration of chemical and genomic spaces. Bioinformatics, 24(13), i232–i240. https://doi.org/10.1093/bioinformatics/btn162
