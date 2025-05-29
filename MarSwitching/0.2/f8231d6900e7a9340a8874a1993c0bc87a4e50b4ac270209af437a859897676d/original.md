```
grid_search_msm(y::VecOrMat{V}, 
                x::VecOrMat{V},
                criterion::String = "AIC";
                k::Vector{Int64} = [2,3,4],
                intercept::Vector{String} = ["switching", "non-switching"],
                vars::Vector{Vector{String}},
                switching_var::Vector{Bool} = [true, false],
                random_n::Int64,
                random_search_em::Int64 = 0,
                random_search::Int64 = 0,
                verbose::Bool = true,
                algorithm::Symbol = :LN_SBPLX,
                maxtime::Int64 = -1) where V <: AbstractFloat
```

Function for exhaustive or random search over specified parameter values for a Markov switching model (currently non-TVTP).

Returns a selected MSM model, vector of criterion values and a vector of tuples containing parameter space.

Note: Unless the data is of small size (both dimensions), it is best to limit the parameter space by providing smaller possible parameters or by chosing random number of parameters to evaluate.

# Arguments

  * `y::VecOrMat{V}`: dependent variable.
  * `x::VecOrMat{V}`: independent variables.
  * `criterion::String`: criterion to use for model selection. One of "AIC" (default) or "BIC".
  * `k::Int64`: vector of states to evaluate.
  * `intercept::String`: vector of "switching", "non-switching" or "no".
  * `vars::Vector{Vector{String}}`: vector of vectors with either "switching" or "non-switching" for corresponding variables in `x` argument.
  * `switching_var::Vector{Bool}`: vector of booleans for variance state dependency.
  * `switching_var::Bool`: is variance state dependent?
  * `random_n::Int64`: number of random parameters combinations to evaluate. If negative, performs an exhaustive grid search.
  * `random_search_em::Int64`: number of random searches to perform for the EM algorithm in eery model estimation. If 0, no random search is performed.
  * `random_search::Int64`: number of random searches to perform.
  * `algorithm::Symbol`: optimization algorithm to use. One of [:LD*VAR2, :LD*VAR1, :LD*LBFGS, :LN*SBPLX]
  * `maxtime::Int64`: maximum time in seconds to run the optimization. If negative, the maximum time is equal T/2.
  * `verbose::Bool`: if true, prints out the progress of the grid/random search.

See also [`MSModel`](@ref).
