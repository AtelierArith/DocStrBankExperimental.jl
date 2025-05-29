```
struct TimeEvolutionHEOMSol
```

A structure storing the results and some information from solving time evolution of hierarchical equations of motion (HEOM).

# Fields (Attributes)

  * `Btier` : The tier (cutoff level) for bosonic hierarchy
  * `Ftier` : The tier (cutoff level) for fermionic hierarchy
  * `times::AbstractVector`: The time list of the evolution.
  * `ados::Vector{ADOs}`: The list of result ADOs at each time point.
  * `expect::Matrix`: The expectation values corresponding to each time point in `times`.
  * `retcode`: The return code from the solver.
  * `alg`: The algorithm which is used during the solving process.
  * `abstol::Real`: The absolute tolerance which is used during the solving process.
  * `reltol::Real`: The relative tolerance which is used during the solving process.
