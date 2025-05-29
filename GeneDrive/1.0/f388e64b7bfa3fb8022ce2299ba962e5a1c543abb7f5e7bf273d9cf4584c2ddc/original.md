```
mutable struct Genetics

    all_genotypes::Array{Drive{<:Genotype}}
    likelihood::Array{Float64, 3}
    S::Vector{Float64}
    Τ::Array{Float64,3}
    Φ::Vector{Float64}
    Ξ_m::Vector{Float64}
    Ξ_f::Vector{Float64}
    Ω::Vector{Float64}
    Β::Vector{Float64}
    Η::Vector{Float64}
    all_wildtypes::Vector{Int64}
    all_modified::Vector{Int64}

        function Genetics(all_genotypes::Array{Drive{<:Genotype}})

            gN = length(all_genotypes)
            likelihood = Array{Float64, 3}(undef, gN, gN, gN)
            S = Vector{Float64}(undef, gN)
            Τ = Array{Float64,3}(undef, gN, gN, gN)
            Φ = Vector{Float64}(undef, gN)
            Ξ_m = Vector{Float64}(undef, gN)
            Ξ_f = Vector{Float64}(undef, gN)
            Ω = Vector{Float64}(undef, gN)
            Β = Vector{Float64}(undef, gN)
            Η = Vector{Float64}(undef, gN)
            all_wildtypes = Vector{Int64}(undef, gN)
            all_modified = Vector{Int64}(undef, gN)

            for (index, g) in enumerate(all_genotypes)
                likelihood[:,:,index] = g.likelihood_slice
                S[index] = g.s
                Τ[:,:,index] = g.τ
                Φ[index] = g.ϕ
                Ξ_m[index] = g.ξ_m
                Ξ_f[index] = g.ξ_f
                Ω[index] = g.ω
                Β[index] = g.β
                Η[index] = g.η
                all_wildtypes[index] = g.wildtype
                all_modified[index] = g.modified
            end

            new(all_genotypes, likelihood, S, Τ, Φ, Ξ_m, Ξ_f, Ω, Β, Η,
            all_wildtypes, all_modified)

        end

end
```

Data for all genotypes in a population.

# Fields

  * `all_genotypes::Array{Drive{<:Genotype}}`: All genotypes in a population.
  * `likelihood::Array{Float64, 3}`: Offspring likelihoods per genotype.
  * `S::Vector{Float64}`: Multiplicative fertility modifier genedata_splitdriveper genotype, applied to oviposition.
  * `Τ::Array{Float64,3}`: Offspring viability per genotype, applied to oviposition.
  * `Φ::Vector{Float64}`: Male to female emergence ratio per genotype.
  * `Ξ_m::Vector{Float64}`: Male pupatory success per genotype.
  * `Ξ_f::Vector{Float64}`: Female pupatory success per genotype.
  * `Ω::Vector{Float64}`: Multiplicative adult mortality modifier per genotype.
  * `Β::Vector{Float64}`: Female fecundity per genotype (count of eggs laid).
  * `Η::Vector{Float64}`: Male mating fitness per genotype.
  * `all_wildtypes::Vector{Int64}`: Collect homozygous wildtype booleans.
  * `all_modified::Vector{Int64}`: Collect homozygous modified booleans.
