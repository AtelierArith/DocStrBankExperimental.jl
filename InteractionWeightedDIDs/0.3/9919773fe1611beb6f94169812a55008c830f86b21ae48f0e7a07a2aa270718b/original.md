```
RegressionBasedDIDResult{TR,CohortInteracted,Haslsweights} <: DIDResult{TR}
```

Estimation results from regression-based difference-in-differences.

# Fields

  * `coef::Vector{Float64}`: coefficient estimates.
  * `vcov::Matrix{Float64}`: variance-covariance matrix for the estimates.
  * `vce::CovarianceEstimator`: variance-covariance estiamtor.
  * `tr::TR`: treatment specification.
  * `pr::AbstractParallel`: parallel trend assumption.
  * `treatweights::Vector{Float64}`: total sample weights from observations for which the corresponding treatment indicator takes one.
  * `treatcounts::Vector{Int}`: total number of observations for which the corresponding treatment indicator takes one.
  * `esample::BitVector`: indicator for the rows from `data` involved in estimation.
  * `nobs::Int`: number of observations involved in estimation.
  * `dof_residual::Int`: residual degree of freedom.
  * `F::Float64`: F-statistic for overall significance of regression model.
  * `p::Float64`: p-value corresponding to the F-statistic.
  * `yname::String`: name of the outcome variable.
  * `coefnames::Vector{String}`: coefficient names.
  * `coefinds::Dict{String, Int}`: a map from `coefnames` to integer indices for retrieving estimates by name.
  * `treatcells::VecColumnTable`: a tabular description of cells where a treatment indicator takes one.
  * `treatname::Symbol`: column name for the variable representing treatment time.
  * `yxterms::Dict{AbstractTerm, AbstractTerm}`: a map from all specified terms to concrete terms.
  * `yterm::AbstractTerm`: the specified term for outcome variable.
  * `xterms::Vector{AbstractTerm}`: the specified terms for covariates and fixed effects.
  * `contrasts::Union{Dict{Symbol, Any}, Nothing}`: contrast coding to be processed by `StatsModels.jl`.
  * `weightname::Union{Symbol, Nothing}`: column name of the sample weight variable.
  * `fenames::Vector{String}`: names of the fixed effects.
  * `nfeiterations::Union{Int, Nothing}`: number of iterations for the fixed effect solver to reach convergence.
  * `feconverged::Union{Bool, Nothing}`: whether the fixed effect solver has converged.
  * `nfesingledropped::Int`: number of singleton observations for fixed effects that have been dropped.
  * `lsweights::Union{TableIndexedMatrix, Nothing}`: cell-level least-square weights.
  * `cellymeans::Union{Vector{Float64}, Nothing}`: cell-level averages of the outcome variable.
  * `cellweights::Union{Vector{Float64}, Nothing}`: total sample weights for each cell.
  * `cellcounts::Union{Vector{Int}, Nothing}`: number of observations for each cell.
