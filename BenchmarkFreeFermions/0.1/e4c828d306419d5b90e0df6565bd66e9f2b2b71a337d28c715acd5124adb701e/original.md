```
 SingleParticleSpectrum(Tij::AbstractMatrix) -> ϵ::Vector{Float64}
```

Numerically diagonalize the hopping matrix `Tij` to get the single particle spectrum `ϵ`. Note the convention is `H = - \sum_ij Tij c_i^dag c_j`.
