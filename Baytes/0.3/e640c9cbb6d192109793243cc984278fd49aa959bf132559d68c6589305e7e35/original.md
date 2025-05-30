```julia
struct Trace{C<:Baytes.TraceSummary, A<:NamedTuple, B}
```

Contains sampling chain and diagnostics for given algorithms.

# Fields

  * `val::Array{Vector{A}, 1} where A<:NamedTuple`: Model samples ~ out vector for corresponding chain, inner vector for iteration
  * `diagnostics::Vector`: Algorithm diagnostics ~ out vector for corresponding chain, inner vector for iteration
  * `summary::Baytes.TraceSummary`: Information about trace used for postprocessing.
