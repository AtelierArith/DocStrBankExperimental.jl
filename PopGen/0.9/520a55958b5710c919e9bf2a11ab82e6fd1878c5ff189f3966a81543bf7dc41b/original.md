```
cutree(::PopData, hcres::Hclust; krange::UnitRange{Int64}, height::Union{Int64, Nothing} = nothing)
cutree(::PopData, hcres::Hclust; krange::Vector{Int64}, height::Union{Int64, Nothing} = nothing)
```

An expansion to the `Clustering.cutree` method (from Clustering.jl) that performs cluster assignments over `krange` on the `Hclust` output from `hclust()`. Returns a `DataFrame` of sample names and columns corresponding to assignments  per k in `krange`. The `PopData` object is used only for retrieving the sample names.

**Keyword Arguments**

  * `krange`: the number of desired clusters, given as a vector (ex. `[2,4,5]`) or range (`2:5`)
  * `h::Integer`: the height at which the tree is cut (optional)
