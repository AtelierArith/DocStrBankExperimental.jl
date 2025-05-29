```
pairwiseidentical(data::PopData, sample_names::Vector{String})
```

Return a pairwise matrix of the percent of identical genotypes at  each nonmissing locus between all pairs of provided `sample_names`.

### Example:

```
julia> cats = @nancycats ;

julia> interesting_cats = samplenames(cats)[1:5]
5-element Array{String,1}:
 "N215"
 "N216"
 "N217"
 "N218"
 "N219"

julia> pairwiseidentical(cats, interesting_cats)
5×5 Named Matrix{Float64}
A ╲ B │     N217      N218      N219      N220      N221
──────┼─────────────────────────────────────────────────
N217  │      1.0       0.0  0.111111  0.222222  0.111111
N218  │      0.0       1.0  0.333333  0.111111  0.444444
N219  │ 0.111111  0.333333       1.0  0.111111  0.333333
N220  │ 0.222222  0.111111  0.111111       1.0  0.222222
N221  │ 0.111111  0.444444  0.333333  0.222222       1.0
```
