```
EpidemicModel
```

Epidemic model containing all the informations of the system.

# Fields

  * `Disease::SmallCouplingDynamicCavity.InfectionModel`: Infection model. Currently are implemented SI, SIR, SIS and SIRS infection models.
  * `G::Union{Vector{<:Graphs.AbstractGraph}, var"#s34"} where var"#s34"<:Graphs.AbstractGraph`: Contact graph. It can be either an AbstractGraph (contact graph constant over time) or a Vector of AbstractGraph (time varying contact graph).
  * `N::Int64`: Number of nodes of the contact graph.
  * `T::Int64`: Number of time steps.
  * `ν::Array{Float64, 3}`: Infection couplings. It is a NVxNVx(T+1) Array where νᵗᵢⱼ=log(1-λᵗᵢⱼ), with λᵗᵢⱼ being the infection probability from individual i to individual j at time t.
  * `obsmat::Matrix{Int8}`: Observations matrix. It is a NVx(T+1) Matrix, where obsᵗᵢ is the observation of individual i at time t: it is equal to -1.0 if not observed, 0.0 if S, 1.0 if I, 2.0 if R (only for SIR and SIRS).
  * `converged::Bool`: Flag to check if the algorithm has converged.
