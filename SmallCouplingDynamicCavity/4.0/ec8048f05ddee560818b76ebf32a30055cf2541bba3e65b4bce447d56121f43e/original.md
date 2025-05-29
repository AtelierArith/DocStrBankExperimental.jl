```
EpidemicModel(
    infectionmodel::TI, 
    G::TG, T::Int, 
    ν::Array{Float64, 3}, 
    obs::Matrix{Int8}) where {TI<:InfectionModel,TG<:Vector{<:AbstractGraph}}
```

Defines the epidemic model.

This function defines an epidemic model based on the provided infection model, contact graph, time steps, infection couplings, and observation matrix.

```
# Arguments
- `infectionmodel`: The infection model. Currently implemented models include SI, SIR, SIS, and SIRS infection models.
- `G`: The contact graph. It should be a T+1 vector of AbstractGraph representing the time-varying contact graph.
- `T`: The number of time-steps.
- `ν`: The infection couplings. It should be a 3-dimensional array of size NVxNVx(T+1), where νᵗᵢⱼ=log(1-λᵗᵢⱼ), with λᵗᵢⱼ being the infection probability from individual i to individual j at time t.
- `obs`: The observations obsmatrix. It should be a NVx(T+1) matrix, where obsᵗᵢ is the observation of individual i at time t: it is equal to -1.0 if not observed, 0.0 if S, 1.0 if I, 2.0 if R (only for SIR and SIRS).

# Returns
- `EpidemicModel`: An [`EpidemicModel`](@ref) object representing the defined epidemic model.
```
