```
emission_distribution(hmm::AbstractHMM, s, par)
```

Compute the emission distribution in state `s` for `hmm` with parameters `par`.

The object returned must be sampleable and implement [DensityInterface.jl](https://github.com/JuliaMath/DensityInterface.jl).
