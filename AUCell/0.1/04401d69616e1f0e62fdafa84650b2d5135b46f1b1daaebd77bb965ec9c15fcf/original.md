```
generate_pseudobulk(mat, np)
```

Generate a matrix of pseudobulk profiles from `mat` which stores single-cell RNA profiles. Each column represents a cell's profile. Each pseudobulk profile is generated from `np` (default: 10) single-cell profiles.

# Examples

```jldoctest
julia> generate_pseudobulk(rand(0:32, 10, 6), 3)
10×2 Matrix{Int64}:
 59  30
 66  34
 37  26
 58  70
 83  86
 15  11
 58  62
 38  62
 62  35
 15  51
```
