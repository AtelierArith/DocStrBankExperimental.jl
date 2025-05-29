```
lossless_modes_dense(pso::PSOModel; min_freq::Real=0,
    max_freq::Union{Real, Nothing}=nothing)
```

Use a dense svd solver to find the modes of the PSOModel neglecting loss. Each mode consists of an eigenvalue `λ` and an eigenvector `v`. The frequency of the mode is `imag(λ)/(2π)` and the decay rate is `-2*real(λ)/(2π)`. `min_freq` and `max_freq` give the frequency range in which to find eigenvalues.
