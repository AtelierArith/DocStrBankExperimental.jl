```
fit(::Type{NetworkLearnerObs}, X, y, Adj, fl_train, fl_exec, fr_train, fr_exec [;kwargs])
```

Training method for the observation-based network learning framework.

# Arguments

  * `X::AbstractMatrix` training data (used by `fl_train`, `fl_exec`; if `use_local_data==true`, it is also used by `fr_train`)
  * `Y::AbstractAray` data targets (used by `fl_train`, `fr_train`)
  * `Adj::Vector{AbstractAdjacency}` a vector containing the observation relational structures (adjacency objects)
  * `fl_train` local model training 'function'; can be anything that supports the call `fl_train((X,y))`
  * `fl_exec` local model prediction 'function'; can be anything that supports the call `fl_exec(Ml,X)` where `Ml = fl_train((X,y))`
  * `fr_train` relational model training `function`; can be anything that suports the call `fr_train((Xr,y))`
  * `fr_exec` relational model prediction `function`; can be anything that suports the call `fr_exec(Mr,Xr)` where `Mr = fr_train((Xr,y))`

and `Xr` is a dataset of relational variables generated by the relational learner using the results of the local model prediction   function and adjacency structures.

# Keyword arguments

  * `priors::Vector{Float64}` class priors (if applicable)
  * `learner::Symbol` relational learner (i.e. variable generator); available options `:rn`, `:wrn`, `:bayesrn` and `:cdrn` (default `:wrn`)
  * `inference::Symbol` collective inference method; available options `:rl`, `:ic` and `:gs` (default `:rl`)
  * `normalize::Bool` whether to normalize the relational variables per-observation to the L1 norm (default `true`)
  * `use_local_data::Bool` whether the relational model should use the local data provided (i.e. in `X`) (default `true`)
  * `f_targets::Function` function that extracts targets from estimates generated by the local/relational models

(default `f_targets = x->MLDataPattern.targets(indmax,x)`)

  * `obsdim::Int` observation dimension (default `2`)
  * `tol::Float64` maximum admissible mean estimate error for collective inference convergence (default `1e-6`)
  * `κ::Float64` relaxation labeling starting constant, used if `learner == :rl` (default `1.0`)
  * `α::Float64` relaxation labeling decay constant, used if `learner == :rl` (default `0.99`)
  * `maxiter::Int` maximum number of iterations for collective inference (default `100`)
  * `bratio::Float64` percentage of iterations i.e. `maxiter` used for Gibbs sampling burn-in (default `0.1`)
