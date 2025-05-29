```
gpss(w, k, t, f; <keyword arguments>)
```

Generalized prolate spheroidal sequences on an unequal grid

...

# Arguments

## Positional Arguments

  * `w::Float64`: the bandwidth
  * `k::Int64`: number of Slepian tapers, must be <=2*bw*length(x)
  * `t::Vector{Int64}`: vector containing the time indices
  * `f::Float64`: frequency at which the tapers are to be computed

## Keyword Arguments

  * `beta::Float64 = 0.5`: analysis half-bandwidth (similar to Nyquist rate)

...

...

# Outputs

  * `lambda::Vector{Float64}` the concentrations of the generalized prolate spheroidal

sequences

  * `u::Matrix{Float64}` the matrix containing the sequences themselves
  * `R` the Cholesky factor for the generalized eigenvalue problem

...

See also: [`mdmultispec`](@ref), [`mdslepian`](@ref)
