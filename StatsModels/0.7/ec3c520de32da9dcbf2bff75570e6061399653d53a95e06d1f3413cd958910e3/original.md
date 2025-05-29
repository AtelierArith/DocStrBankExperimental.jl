```
SeqDiffCoding([base[, levels]])
```

Code each level in order to test "sequential difference" hypotheses, which compares each level to the level below it (starting with the second level). Specifically, the $n$th predictor tests the hypothesis that the difference between levels $n$ and $n+1$ is zero.

Differences are computed in order of `levels`.  If `levels` are omitted or `nothing`, they are determined from the data by calling the `levels` function when constructing `ContrastsMatrix`. If `base` is omitted or `nothing`, the first level is used as the base.

# Examples

```jldoctest seqdiff
julia> seqdiff = StatsModels.ContrastsMatrix(SeqDiffCoding(), ["a", "b", "c", "d"]).matrix
4×3 Matrix{Float64}:
 -0.75  -0.5  -0.25
  0.25  -0.5  -0.25
  0.25   0.5  -0.25
  0.25   0.5   0.75
```

The interpretation of sequential difference coding may be hard to see from the contrasts matrix itself.  The corresponding hypothesis matrix shows a clearer picture.  From the rows of the hypothesis matrix, we can see that these contrasts test the difference between the first and second levels, the second and third, and the third and fourth, respectively:

```jldoctest seqdiff
julia> StatsModels.hypothesis_matrix(seqdiff)
3×4 Matrix{Int64}:
 -1   1   0  0
  0  -1   1  0
  0   0  -1  1
```
