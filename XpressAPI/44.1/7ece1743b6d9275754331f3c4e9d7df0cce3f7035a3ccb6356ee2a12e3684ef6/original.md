```
XPRSrepairweightedinfeasbounds(prob, lepref, gepref, lbpref, ubpref, lerelax, gerelax, lbrelax, ubrelax, phase2, delta, flags)::status
```

An extended version of XPRSrepairweightedinfeas that allows for bounding the level of relaxation allowed.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `lepref::AbstractVector{Number}`: Array of size `ROWS` containing the preferences for relaxing the less or equal side of row.
  * `gepref::AbstractVector{Number}`: Array of size `ROWS` containing the preferences for relaxing the greater or equal side of a row.
  * `lbpref::AbstractVector{Number}`: Array of size `COLS` containing the preferences for relaxing lower bounds.
  * `ubpref::AbstractVector{Number}`: Array of size `COLS` containing preferences for relaxing upper bounds.
  * `lerelax::AbstractVector{Number}`: Array of size `ROWS` containing the upper bounds on the amount the less or equal side of a row can be relaxed.
  * `gerelax::AbstractVector{Number}`: Array of size `ROWS` containing the upper bounds on the amount the greater or equal side of a row can be relaxed.
  * `lbrelax::AbstractVector{Number}`: Array of size `COLS` containing the upper bounds on the amount the lower bounds can be relaxed.
  * `ubrelax::AbstractVector{Number}`: Array of size `COLS` containing the upper bounds on the amount the upper bounds can be relaxed.
  * `phase2::Integer`: Controls the second phase of optimization: ouse the objective sense of the original problem (default); xmaximize the relaxed problem using the original objective; fskip optimization regarding the original objective; nminimize the relaxed problem using the original objective; iif the relaxation is infeasible, generate an irreducible infeasible subset for the analys of the problem; aif the relaxation is infeasible, generate all irreducible infeasible subsets for the analys of the problem.
  * `delta::Float64`: The relaxation multiplier in the second phase -1.
  * `flags::Union{Nothing,AbstractString}`: Specifies flags to be passed to the Optimizer.

# Return value

  * `status::Int32`: The status after the relaxation: 1relaxed problem is infeasible; 2relaxed problem is unbounded; 3solution of the relaxed problem regarding the original objective is nonoptimal; 4error (when return code is nonzero); 5numerical instability; 6analysis of an infeasible relaxation was performed, but the relaxation is feasible.

See also the documentation of the correponding function [XPRSrepairweightedinfeasbounds](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrepairweightedinfeasbounds.html) in the C API.
