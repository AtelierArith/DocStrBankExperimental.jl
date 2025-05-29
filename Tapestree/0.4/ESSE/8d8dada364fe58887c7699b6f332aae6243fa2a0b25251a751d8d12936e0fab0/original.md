```
simulate_sse(λ          ::Array{Float64,1},
             μ          ::Array{Float64,1},
             l          ::Array{Float64,1},
             g          ::Array{Float64,1},
             q          ::Array{Float64,1},
             β          ::Array{Float64,1},
             t          ::Float64,
             x          ::Array{Float64,1},
             y          ::Array{Float64,N},
             cov_mod    ::Tuple{Vararg{String}};
             δt         ::Float64 = 1e-4,
             ast        ::Int64   = 0,
             nspp_max   ::Int64   = 100_000,
             retry_ext  ::Bool    = true,
             rejectel0  ::Bool    = true,
             verbose    ::Bool    = true,
             rm_ext     ::Bool    = true,
             states_only::Bool    = false,
             start      ::Symbol  = :crown) where {N}
```

Simulate tree according to the geographic **sse** model. The number of areas  and hidden states is inferred from the parameter vectors, but they must be  consistent between them and with the covariates. See tutorial for an example.

# Arguments

  * `λ::Array{Float64,1}`: rates for within-area and between-area speciation.
  * `μ::Array{Float64,1}`: per-area extinction rates when it leads to global

extinction.

  * `l::Array{Float64,1}`: per-area extinction rates when it leads to local

extinction.

  * `g::Array{Float64,1}`: colonization rates between areas.
  * `q::Array{Float64,1}`: transition rates between hidden states.
  * `β::Array{Float64,1}`: per-area effect of covariates.
  * `t::Float64`: simulation time.
  * `x::Array{Float64,1}`: times where the covariate `y` is sampled.
  * `y::Array{Float64,N}`: value of covariates, i.e., `f(x)`. Can be multivariate.
  * `cov_mod::Tuple{Vararg{String}}`: specifies which rates are affected by

covariates: `s` for speciation, `e` for extinction, and `g` for colonization. More than 1 is possible. 

  * `δt::Float64 = 1e-4`: time step to perform simulations. Smaller more precise

but more computationally expensive.

  * `ast::Int64 = 0`: initial state. `0` specifies random sampling based on the

input parameters.

  * `nspp_max::Int64 = 100_000`: maximum number of species allowed to stop

simulation.

  * `retry_ext::Bool = true`: automatically restart simulation if simulation goes

extinct.

  * `rejectel0::Bool = true`: reject simulations where there are edges of 0

length.

  * `verbose::Bool = true`: print messages.
  * `rm_ext::Bool = true`: remove extinct taxa from output.
  * `states_only::Bool = false`: if only return tip states (faster).
  * `start::Symbol  = :crown`: if `crown`, starts after a speciation event with

two lineages, if `stem`, starts with one lineage.

# Returned values

  * Dictionary with tip number and corresponding state.
  * Array with parent -> daughter edges.
  * Array with edge lengths.
  * Number of maximum species.
