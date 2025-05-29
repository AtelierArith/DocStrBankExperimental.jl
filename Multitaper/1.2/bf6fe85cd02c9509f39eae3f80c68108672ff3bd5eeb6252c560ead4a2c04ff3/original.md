```
mdslepian(w, k, t)
```

Generalized prolate spheroidal sequences for the 1D missing data problem

...

# Arguments

## Positional Arguments

  * `w::Float64`: the bandwidth
  * `k::Int64`: number of Slepian tapers, must be <=2*bw*length(x)
  * `t::Vector{Int64}`: vector containing the time indices

...

...

# Outputs

  * `lambda,u::Tuple{Vector{Float64}, Vector{Float64}}`: tuple containing the

concentrations and the tapers

...

See also: [`mdmultispec`](@ref), [`gpss`](@ref)
