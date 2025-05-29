```
mutable struct ProportionalRelease <: Intervention
    node::Symbol
    organism::Type{<:Species}
    stage::Type{<:LifeStage}
    gene_index::Int64
    times::Vector{Float64}
    proportion::Float64
    callbacks::Vector
    adults_counting::String
end
```

Data for biological control interventions predicated on releasing modified organisms.

# Arguments

  * `node::Symbol`: `Node` where releases occur.
  * `organism::Type{<:Species}`: Species of organism being released.
  * `stage::Type{<:LifeStage}`: `LifeStage` of organism being released.
  * `gene_index::Int64`: Genotype being released to implement the intervention.
  * `times::Vector{Float64}`: Release time points.
  * `proportion::Float64`: Proportion of modified organisms released during each time period.
  * `callbacks::Vector`
  * `adults_to_count::String`: The `LifeStage` of the standing population against which to measure proportional release size. Choices include `Male`, `Female`, or `All`.
