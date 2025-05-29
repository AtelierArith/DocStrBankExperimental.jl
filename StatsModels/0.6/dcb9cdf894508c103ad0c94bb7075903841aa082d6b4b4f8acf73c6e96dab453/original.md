```
StatsModels.ContrastsCoding(mat::AbstractMatrix[, levels]])
StatsModels.ContrastsCoding(mat::AbstractMatrix[; levels=nothing])
```

Coding by manual specification of contrasts matrix. For k levels, the contrasts must be a k by k-1 Matrix.  The contrasts in this matrix will be copied directly into the model matrix; if you want to specify your contrasts as hypotheses (i.e.,  weights assigned to each level's cell mean), you should use  [`HypothesisCoding`](@ref) instead.
