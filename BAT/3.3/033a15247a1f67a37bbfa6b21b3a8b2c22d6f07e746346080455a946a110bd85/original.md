```
OptimAlg
```

Selects an optimization algorithm from the [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl) package.

Note that when using first order algorithms like `Optim.LBFGS`, your [`BATContext`](@ref) needs to include an `ADSelector` that specifies which automatic differentiation backend should be used.

Constructors:

  * `OptimAlg(; fields...)`

`optimalg` must be an `Optim.AbstractOptimizer`.

Fields:

  * `optalg::Any`: Default: ext*default(pkgext(Val(:Optim)), Val(:DEFAULT*OPTALG))
  * `trafo::BAT.AbstractTransformTarget`: Default: PriorToGaussian()
  * `init::BAT.InitvalAlgorithm`: Default: InitFromTarget()
  * `maxiters::Int64`: Default: 1000
  * `maxtime::Float64`: Default: NaN
  * `abstol::Float64`: Default: NaN
  * `reltol::Float64`: Default: 0.0
  * `kwargs::NamedTuple`: Default: (;)

!!! note
    This algorithm is only available if the Optim package is loaded (e.g. via     `import Optim`.

