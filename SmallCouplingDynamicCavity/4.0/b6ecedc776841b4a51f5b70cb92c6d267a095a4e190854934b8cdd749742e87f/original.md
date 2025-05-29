```
EpidemicModel(
    infectionmodel::TI, 
    G::TG, T::Int, 
    ν::Array{Float64, 3}) where {TI<:InfectionModel,TG<:Vector{<:AbstractGraph}}
```

Define an epidemic model.

This function defines an epidemic model based on the provided infection model, time-varying contact graph, time steps, and infection couplings. It initializes the observation matrix with zeros.

# Arguments

  * `infectionmodel`: The infection model. Currently implemented models include SI, SIR, SIS, and SIRS infection models.
  * `G`: The contact graph. It should be a T+1 vector of AbstractGraph representing the time-varying contact graph.
  * `T`: The number of time-steps.
  * `ν`: The infection couplings. It should be a 3-dimensional array of size NVxNVx(T+1), where νᵗᵢⱼ=log(1-λᵗᵢⱼ), with λᵗᵢⱼ being the infection probability from individual i to individual j at time t.

# Returns

  * `EpidemicModel`: An [`EpidemicModel`](@ref) object representing the defined epidemic model.
