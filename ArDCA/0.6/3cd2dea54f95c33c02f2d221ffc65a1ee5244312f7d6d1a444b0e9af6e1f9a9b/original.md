```
ardca(filename::String; kwds...)
```

Run [`ardca`](@ref) on the fasta alignment in `filename`

Return two `struct`: `::ArNet` (containing the inferred hyperparameters) and `::ArVar`

Optional arguments:

  * `max_gap_fraction::Real=0.9` maximum fraction of insert in the sequence
  * `remove_dups::Bool=true` if `true` remove duplicated sequences
  * `theta=:auto` if `:auto` compute reweighint automatically. Otherwise set a `Float64` value `0 ≤ theta ≤ 1`
  * `lambdaJ::Real=0.01` coupling L₂ regularization parameter (lagrange multiplier)
  * `lambdaH::Real=0.01` field L₂ regularization parameter (lagrange multiplier)
  * `pc_factor::Real=1/size(Z,2)` pseudocount factor for calculation of `p0`, defaults to one over the number of sequences.
  * `epsconv::Real=1.0e-5` convergence value in minimzation
  * `maxit::Int=1000` maximum number of iteration in minimization
  * `verbose::Bool=true` set to `false` to stop printing convergence info on `stdout`
  * `method::Symbol=:LD_LBFGS` optimization strategy see [`NLopt.jl`](https://github.com/JuliaOpt/NLopt.jl) for other options
  * `permorder::Union{Symbol,Vector{Ti}}=:ENTROPIC` permutation order. Possible values are `:NATURAL,:ENTROPIC,:REV_ENTROPIC,:RANDOM` or a custom permutation vector

# Examples

```
julia> arnet, arvar =  ardca("pf14.fasta", permorder=:ENTROPIC)
```
