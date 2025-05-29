```
modelmatrices(X::AbstractDesignMatrix)
modelmatrices(X::Vector{<:AbstractDesignMatrix})
modelmatrices(modelmatrix::AbstractMatrix)
```

Returns the modelmatrices (also called designmatrices) separately for the events. This is similar to `StatsModels.modelcols`, but merely access the precomputed designmatrix. If the designmatrix needs to be computed, please use `modelcols`

Compare to `modelmatrix` which further concatenates the designmatrices (in the ContinuousTime case).
