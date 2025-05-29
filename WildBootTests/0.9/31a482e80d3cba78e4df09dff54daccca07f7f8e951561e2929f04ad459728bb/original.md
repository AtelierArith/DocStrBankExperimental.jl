wildboottest([T::DataType=Float64,] R::AbstractMatrix, r::AbstractVector;               resp, <optional keyword arguments>) -> WildBootTests.BootTestResult

Function to perform wild-bootstrap-based hypothesis test

# Positional arguments

  * `T::DataType`: data type for inputs, results, and computations: Float32 or Float64 (default)
  * `R::AbstractMatrix` and `r::AbstractVector`: required matrix and vector expressing the null Rβ=r; see notes below

# Required keyword argument

  * `resp::AbstractVector`: response/dependent variable (y or y₁ in Roodman et al. (2019))

# Optional keyword arguments

  * `predexog::AbstractVecOrMat`: exogenous predictors, including constant term, if any (X/X₁)
  * `predendog::AbstractVecOrMat`: endogenous predictors (Y₂)
  * `inst::AbstractVecOrMat`: instruments (X₂)
  * `R1::AbstractMatrix` and `r1::AbstractVector`: model constraints; same format as for `R` and `r`
  * `clustid::AbstractVecOrMat{<:Integer}`: data vector/matrix of error and bootstrapping cluster identifiers; see notes
  * `nbootclustvar::Integer=size(clustid,2)`: number of bootstrap-clustering variables
  * `nerrclustvar::Integer=nbootclustvar`: number of error-clustering variables
  * `issorted:Bool=false`: time-saving flag: data matrices are already sorted by column types 2, then 3, then 1 (see notes)
  * `hetrobust::Bool=true`: true unless errors are treated as iid
  * `feid::AbstractVector{<:Integer}`: data vector for one-way fixed effect group identifier
  * `fedfadj::Integer`: degrees of freedom that fixed effects (if any) consume; defaults to number of FEs
  * `obswt::AbstractVector=[]`: observation weight vector; default is equal weighting
  * `fweights::Bool=false`: true for frequency weights
  * `maxmatsize::Number`: maximum size of auxilliary weight matrix (v), in gigabytes
  * `ptype::Symbol=:symmetric`: p value type (`:symmetric`, `:equaltail`, `:lower`, `:upper`)
  * `bootstrapc::Bool=false`: true to request bootstrap-c instead of bootstrap-t
  * `liml::Bool=false`: true for LIML or Fuller LIML
  * `fuller::Number`: Fuller LIML factor
  * `kappa::Number`: fixed κ for *k*-class estimation
  * `arubin::Bool=false`: true for Anderson-Rubin test
  * `small::Bool=true`: true to multiply test statistics by G/(G-1) × N/(N-k), where G, N, k are number of clusters, observations, and predictors
  * `clusteradj::Bool=true`: false to drop G/(G-1) factor
  * `clustermin::Bool=false``: for multiway clustering, true to base G/(G-1) factor for all clusterings ]on the smallest G across clusterings
  * `jk::Bool=false`: true to base the bootstrap data-generating process on residuals jackknifed by bootstrap cluster
  * `scorebs::Bool=false`: true for score bootstrap instead of wild bootstrap
  * `reps::Integer=999`: number of bootstrap replications; `reps` = 0 requests classical Rao (or Wald) test if `imposenull` = `true` (or `false`)
  * `imposenull::Bool=true`: true to impose null
  * `auxwttype::Symbol=:rademacher`: auxilliary weight type (`:rademacher`, `:mammen`, `:webb`, `:normal`, `:gamma`)
  * `rng::AbstractRNG=MersenneTwister()`: randon number generator
  * `level::Number=.95`: significance level (0-1)
  * `rtol::Number=1e-3`: tolerance for confidence set bound determination
  * `madjtype::Symbol=:none`: multiple hypothesis adjustment (`:none`, `:bonferroni`, `:sidak`)
  * `nH0::Integer=1`: number of hypotheses tested, including one being tested now
  * `ml::Bool=false`: true for (nonlinear) ML estimation
  * `scores::AbstractVecOrMat`: for ML, pre-computed scores
  * `beta::AbstractVector`: for ML, parameter estimates
  * `A::AbstractMatrix`: for ML, covariance estimates
  * `gridmin`: vector of graph lower bounds; max length 2, `missing`/`NaN` entries ask wildboottest() to choose
  * `gridmax`: vector of graph upper bounds; `missing`/`NaN` entries ask wildboottest() to choose
  * `gridpoints`: vector of number of sampling points; `missing`/`NaN` entries ask wildboottest() to choose
  * `getdist::Bool=:false`: whether to return bootstrapped distribution for t/z/F/χ² statistics; and their numerators
  * `getci::Bool=true`: whether to return confidence interval
  * `getplot::Bool=getci`: whether to generate plot data
  * `getauxweights::Bool=false`: whether to save auxilliary weight matrix (v)

# Notes

`T`, `ptype`, `auxwttype`, and `madjtype` may also be strings. Examples: `"Float32"` and `"webb"`.

The columns of `R` in the statement of the null should correspond to those of the matrix [`predexog` `predendog`], where `predendog` is non-empty only in regressions with instruments. 

Order the columns of `clustid` this way:

1. Variables only used to define bootstrapping clusters, as in the subcluster bootstrap.
2. Variables used to define both bootstrapping and error clusters.
3. Variables only used to define error clusters.

`nbootclustvar` is then the number of columns of type 1 or 2; `nerrclustvar` is the number of columns of type 2 or 3. Typically `clustid` is a single column of type 2 and `nbootclustvar` and `nerrclustvar` default to 1.

`wildboottest()` does not handle missing data values: all data and identifier matrices must  be restricted to the estimation sample.
