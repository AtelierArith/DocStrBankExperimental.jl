```
RelativePartialRandomization(α = 0.5)
```

`RelativePartialRandomization` surrogates are similar to [`PartialRandomization`](@ref) phase surrogates, but instead of drawing phases uniformly from `[0, 2π]`, phases are drawn from `ϕ + [0, 2π]*α`, where `α ∈ [0, 1]` and `ϕ` is the original Fourier phase.

See the documentation for a detailed comparison between partial randomization algorithms.
