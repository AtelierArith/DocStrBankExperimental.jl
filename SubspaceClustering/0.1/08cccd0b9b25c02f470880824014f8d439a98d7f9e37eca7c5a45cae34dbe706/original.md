```
KSSResult{
    TU<:AbstractVector{<:AbstractMatrix{<:AbstractFloat}},
    Tc<:AbstractVector{<:Integer},
    T<:Real}
```

The output of [`kss`](@ref).

# Fields

  * `U::TU`: vector of subspace basis matrices `U[1],...,U[K]`
  * `c::Tc`: vector of cluster assignments `c[1],...,c[N]`
  * `iterations::Int`: number of iterations performed
  * `totalcost::T`: final value of total cost function
  * `counts::Vector{Int}`: vector of cluster sizes `counts[1],...,counts[K]`
  * `converged::Bool`: final convergence status
