```
PseudoPeriodic(d, τ, ρ, shift = true)
```

Create surrogates suitable for pseudo-periodic signals. They retain the periodic structure of the signal, while inter-cycle dynamics that are either deterministic or correlated noise are destroyed (for appropriate `ρ` choice). Therefore these surrogates are suitable to test the null hypothesis that the signal is a periodic orbit with uncorrelated noise[^Small2001].

Arguments `d, τ, ρ` are as in the paper, the embedding dimension, delay time and noise radius. The method works by performing a delay coordinates embedding from DelayEmbeddings.jl (see that docs for choosing appropriate `d, τ`). For `ρ`, we have implemented the method proposed in the paper in the function [`noiseradius`](@ref).

The argument `shift` is not discussed in the paper. If `shift=false` we adjust the algorithm so that there is little phase shift between the periodic component of the original and surrogate data.

See also [`CycleShuffle`](@ref).

[^Small2001]: Small et al., Surrogate test for pseudoperiodic time series data, [Physical Review Letters, 87(18)](https://doi.org/10.1103/PhysRevLett.87.188101)
