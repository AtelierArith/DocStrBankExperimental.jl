```
MSModel(y::VecOrMat{V},
        k::Int64, 
        ;intercept::String = "switching",
        exog_vars::VecOrMat{V},
        exog_switching_vars::VecOrMat{V},
        switching_var::Bool = true,
        exog_tvtp::VecOrMat{V},
        x0::Vector{V},
        algorithm::Symbol = :LN_SBPLX,
        maxtime::Int64 = -1,
        random_search::Int64 = 0,
        random_search_em::Int64,
        verbose::Bool) where V <: AbstractFloat
```

Function to estimate the Markov Switching Model. Returns an instance of MSM struct.

Note: The model likelihood function is very nonlinear and prone to local maxima. Increasing number of random searches can help, for the cost of longer training time. For the same reason, it is recommended not to estimate model with many states (e.g. more than 5), altough it is possible.

# Arguments

  * `y::VecOrMat{V}`: dependent variable.
  * `k::Int64`: number of states.
  * `intercept::String`: "switching" or "non-switching" or "no".
  * `exog_vars::VecOrMat{V}`: optional exogenous variables for the non-switching part of the model.
  * `exog_switching_vars::VecOrMat{V}`: optional exogenous variables for the switching part of the model.
  * `switching_var::Bool`: is variance state dependent?
  * `exog_tvtp::VecOrMat{V}`: optional exogenous variables for the tvtp part of the model.
  * `x0::Vector{V}`: initial guess for the parameters. If empty, the initial guess is generated from k-means clustering.
  * `algorithm::Symbol`: optimization algorithm to use. One of [`:LD_VAR2`, `:LD_VAR1`, `:LD_LBFGS`, `:LN_SBPLX`]
  * `maxtime::Int64`: maximum time in seconds to run the optimization. If negative, the maximum time is equal T/2.
  * `random_search_em::Int64`: number of random searches to perform for the EM algorithm. If 0, no random search is performed.
  * `random_search::Int64`: number of random searches to perform.
  * `verbose::Bool`: if true, prints out the progress of the random searches.

References:

  * Hamilton, J. D. (1989). A new approach to the economic analysis of nonstationary time series and the business cycle. Econometrica: Journal of the Econometric Society, 357-384.
  * Filardo, Andrew J. (1994). Business cycle phases and their transitional dynamics. Journal of Business & Economic Statistics, 12(3), 299-308.

See also [`grid_search_msm`](@ref).
