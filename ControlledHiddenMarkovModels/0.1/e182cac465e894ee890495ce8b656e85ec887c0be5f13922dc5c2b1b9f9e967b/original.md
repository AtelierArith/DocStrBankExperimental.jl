```
emission_distribution(hmm::AbstractControlledHMM, s, θ)
```

Compute the emission distribution in state `s` for `hmm` with emission parameters `θ`. Note that `θ` was computed using [`emission_parameters(hmm, control, par)`](@ref).

The object returned must be sampleable and implement [DensityInterface.jl](https://github.com/JuliaMath/DensityInterface.jl).
