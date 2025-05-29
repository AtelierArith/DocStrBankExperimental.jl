```
SpectralSpectralPartialRandomization(α = 0.5)
```

`SpectralPartialRandomization` surrogates are similar to [`PartialRandomization`](@ref) phase surrogates, but instead of drawing phases uniformly from `[0, 2π]`, phases of the highest frequency components responsible for a proportion `α` of power are replaced by random phases drawn from `[0, 2π]`

See the documentation for a detailed comparison between partial randomization algorithms.
