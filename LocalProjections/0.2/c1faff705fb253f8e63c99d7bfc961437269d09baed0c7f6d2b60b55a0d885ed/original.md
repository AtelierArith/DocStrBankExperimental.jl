```
GridSearchResult{TF<:AbstractFloat} <: ModelSelectionResult
```

Additional results from [`GridSearch`](@ref), including estimates calculated for each parameter on the grid.

# Fields

  * `iopt::Dict{SearchCriterion,Int}`: index of the optimal parameter based on each criterion.
  * `θs::Matrix{TF}`: point estimates obtained.
  * `loocv::Vector{TF}`: leave-one-out cross validation errors.
  * `rss::Vector{TF}`: residual sums of squares.
  * `gcv::Vector{TF}`: generalized cross validation errors.
  * `aic::Vector{TF}`: Akaike information criterion values.
  * `dof_fit::Vector{TF}`: degrees of freedom of the fit.
  * `dof_res::Vector{TF}`: residual degrees of freedom.
