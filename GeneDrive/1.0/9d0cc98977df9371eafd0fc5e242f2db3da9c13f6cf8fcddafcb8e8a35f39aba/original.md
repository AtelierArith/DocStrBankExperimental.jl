```
mutable struct Drive{G <: Genotype}
    genotype::Type{G}
    likelihood_slice::Array{Float64,2}
    s::Float64
    τ::Array{Float64,2}
    ϕ::Float64
    ξ_m::Float64
    ξ_f::Float64
    ω::Float64
    β::Float64
    η::Float64
    wildtype::Int64
    modified::Int64
end
```

Data for individual genotypes.

# Fields

  * `genotype::Type{G}`: Single genotype.
  * `likelihood_slice::Array{Float64,2}`: Offspring likelihoods for this genotype.
  * `s::Float64`: Multiplicative fertility modifier.
  * `τ::Array{Float64,2}`: Offspring viability.
  * `ϕ::Float64`: Male to female emergence ratio.
  * `ξ_m::Float64`: Male pupatory success.
  * `ξ_f::Float64`: Female pupatory success.
  * `ω::Float64`: Multiplicative adult mortality modifier.
  * `β::Float64`: Female fecundity.
  * `η::Float64`: Male mating fitness.
  * `wildtype::Int64`: Boolean demarcates homozygous recessive.
  * `modified::Int64`: Boolean demarcates homozygous modified.
