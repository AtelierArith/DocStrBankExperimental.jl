```
mutable struct Release <: Intervention
    node::Symbol
    organism::Type{<:Species}
    stage::Type{<:LifeStage}
    gene_index::Int64
    times::Vector{Float64}
    values::Vector{Float64}
    callbacks::Vector
end
```

Data for biological control interventions predicated on releasing modified organisms. Applicable to both suppression and replacement techniques.

# Arguments

  * `node::Symbol`: `Node` where releases occur.
  * `organism::Type{<:Species}`: Species of organism being released.
  * `stage::Type{<:LifeStage}`: `Life stage` of organism being released.
  * `gene_index::Int64`: Genotype being released to implement the intervention.
  * `times::Vector{Float64}`: Release time points.
  * `values::Union{Float64, Vector{Float64}}`: Number of modified organisms released during each time period. Variably sized releases permitted.
  * `callbacks::Vector`
