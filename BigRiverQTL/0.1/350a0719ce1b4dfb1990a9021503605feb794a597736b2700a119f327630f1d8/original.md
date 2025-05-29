```
calckinship(geno::Matrix{Float64})
```

Calculate kinship from the genotype probability array.

# Arguments

  * `geno` is the genotype probability matrix for n individuals and p markers.

# Output

Returns a n x n symmetric matrix containing 1's on the diagonal.

___

calckinship(geno::Matrix{Union{Missing,Float64}})

Calculate kinship from the genotype probability array.

# Arguments

  * `geno` is the genotype probability matrix, n individuals and p markers, which    contains `missing` values.

# Output

Returns a n x n symmetric matrix containing 1's on the diagonal.
