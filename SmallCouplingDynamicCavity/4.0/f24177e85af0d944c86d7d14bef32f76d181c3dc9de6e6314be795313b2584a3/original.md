```
struct SI <: InfectionModel
    εᵢᵗ::Array{Float64, 2} # Autoinfection probabilities
end
```

The `SI` struct represents the SI (Susceptible-Infected) infection model.

# Fields

  * `εᵢᵗ`: An NVxT array representing the self-infection probabilities over time, where NV is the number of nodes and T is the number of time-steps. Each element εᵢᵗ[i, t] denotes the probability of node i infecting itself at time t.
