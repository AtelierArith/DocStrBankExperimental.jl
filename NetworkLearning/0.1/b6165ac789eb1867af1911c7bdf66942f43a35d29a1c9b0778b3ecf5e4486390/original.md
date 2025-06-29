```
fit(::Type{NetworkLearnerEnt}, X, update, Adj, fl_train, fl_exec, fr_train, fr_exec [;kwargs])
```

Training method for the entity-based network learning framework.

# Arguments

  * `Xo::AbstractMatrix` initial estimates for the entities
  * `update::BitVector` mask that indicates wether estimates can be updated (`true` value) or not (`false` value); false values

generally can be associated with estimates of training samples

  * `Adj::Vector{AbstractAdjacency}` a vector containing the entity relational structures (adjacency objects)
  * `fr_train` relational model training `function`; can be anything that suports the call `fr_train((Xr,y))` where `y = f_targets(Xo)`
  * `fr_exec` relational model prediction `function`; can be anything that suports the call `fr_exec(Mr,Xr)` where `Mr = fr_train((Xr,y))`

and `Xr` is a dataset of relational variables generated by the relational learner using the estimates `Xo` and the  adjacency structures.

# Keyword arguments

  * `priors::Vector{Float64}` class priors (if applicable)
  * `learner::Symbol` relational learner (i.e. variable generator); available options `:rn`, `:wrn`, `:bayesrn` and `:cdrn` (default `:wrn`)
  * `inference::Symbol` collective inference method; available options `:rl`, `:ic` and `:gs` (default `:rl`)
  * `normalize::Bool` whether to normalize the relational variables per-entity to the L1 norm (default `true`)
  * `f_targets::Function` function that extracts targets from estimates generated by the local/relational models

(default `f_targets = x->MLDataPattern.targets(indmax,x)`)

  * `obsdim::Int` observation dimension (default `2`)
  * `tol::Float64` maximum admissible mean estimate error for collective inference convergence (default `1e-6`)
  * `κ::Float64` relaxation labeling starting constant, used if `learner == :rl` (default `1.0`)
  * `α::Float64` relaxation labeling decay constant, used if `learner == :rl` (default `0.99`)
  * `maxiter::Int` maximum number of iterations for collective inference (default `100`)
  * `bratio::Float64` percentage of iterations i.e. `maxiter` used for Gibbs sampling burn-in (default `0.1`)
