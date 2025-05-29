```
struct SIRS <: InfectionModel
    εᵢᵗ::Array{Float64, 2} # Autoinfection probabilities
    rᵢᵗ::Array{Float64, 2} # Recovery probabilities
    σᵢᵗ::Array{Float64, 2} # Loss of immunity probabilities
end
```

The `SIRS` struct represents the SIRS (Susceptible-Infected-Recovered-Susceptible) infection model.

# Fields

  * `εᵢᵗ`: An NVxT array representing the self-infection probabilities over time, where NV is the number of nodes and T is the number of time-steps. Each element εᵢᵗ[i, t] denotes the probability of node i infecting itself at time t.
  * `rᵢᵗ`: An NVxT array representing the recovery probabilities over time, where NV is the number of nodes and T is the number of time-steps. Each element rᵢᵗ[i, t] denotes the probability of node i recovering from infection at time t.
  * `σᵢᵗ`: An NVxT array representing the loss of immunity probabilities over time, where NV is the number of nodes and T is the number of time-steps. Each element σᵢᵗ[i, t] denotes the probability of node i losing immunity and becoming susceptible again at time t.
