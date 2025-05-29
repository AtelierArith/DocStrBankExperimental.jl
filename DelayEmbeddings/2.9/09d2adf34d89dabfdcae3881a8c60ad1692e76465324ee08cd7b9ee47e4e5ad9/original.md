```
delay_ifnn(s::Vector, τ::Int, ds = 1:10; kwargs...) → `FNNs`
```

Compute and return the `FNNs`-statistic for the time series `s` and a uniform time delay `τ` and embedding dimensions `ds` after [^Hegger1999]. In this notation `γ ∈ γs = d-1`, if `d` is the embedding dimension. This fraction tends to 0 when the optimal embedding dimension with an appropriate lag is reached.

## Keywords

*`r = 2`: Obligatory threshold, which determines the maximum tolerable spreading     of trajectories in the reconstruction space. *`metric = Euclidean`: The norm used for distance computations. *`w = 1` = The [Theiler window](@ref).

See also: [`optimal_separated_de`](@ref).
