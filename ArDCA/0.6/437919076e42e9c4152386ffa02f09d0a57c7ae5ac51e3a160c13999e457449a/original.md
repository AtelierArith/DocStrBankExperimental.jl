```
ardca(Z::Array{Ti,2},W::Vector{Float64}; kwds...)
```

Auto-regressive analysis on the L×M alignment `Z` (numerically encoded in 1,…,21), and the `M`-dimensional normalized  weight vector `W`.

Return two `struct`: `::ArNet` (containing the inferred hyperparameters) and `::ArVar`

Optional arguments:

  * `lambdaJ::Real=0.01` coupling L₂ regularization parameter (lagrange multiplier)
  * `lambdaH::Real=0.01` field L₂ regularization parameter (lagrange multiplier)
  * `pc_factor::Real=0` pseudocount factor for calculation of `p0`, defaults to one over the number of sequences.
  * `epsconv::Real=1.0e-5` convergence value in minimzation
  * `maxit::Int=1000` maximum number of iteration in minimization
  * `verbose::Bool=true` set to `false` to stop printing convergence info on `stdout`
  * `method::Symbol=:LD_LBFGS` optimization strategy see [`NLopt.jl`](https://github.com/JuliaOpt/NLopt.jl) for other options
  * `permorder::Union{Symbol,Vector{Ti}}=:ENTROPIC` permutation order. Possible values are `:NATURAL,:ENTROPIC,:REV_ENTROPIC,:RANDOM` or a custom permutation vector

# Examples

```
julia> arnet, arvar= ardca(Z,W,lambdaJ=0,lambdaH=0,permorder=:REV_ENTROPIC,epsconv=1e-12);
```
