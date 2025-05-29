```
struct AtomicMeasure{T, AT, V} <: AbstractMeasureLike{T}
    variables::V                           # Vector/Tuple of variables
    atoms::Vector{WeightedDiracMeasure{T, AT}} # Atoms of the measure
end
```

An measure is said to be *atomic* if it is a sum of weighted dirac measures. For instance, $\eta = 2 \delta_{(1, 0)} + 3 \delta_{(1/2, 1/2)}$ is an atomic measure since it is a sum of the diracs centered at $(1, 0)$ and $(1/2, 1/2)$ and weighted respectively by 2 and 3. That is, $\mathbb{E}_{\eta}[p] = 2p(1, 0) + 3p(1/2, 1/2)$.

The `AtomicMeasure` struct stores an atomic measure where `variables` contains the variables and `atoms` contains atoms of the measure.
