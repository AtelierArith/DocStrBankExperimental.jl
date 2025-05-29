```
lossy_modes_dense(pso::PSOModel; min_freq::Real=0,
    max_freq::Union{Real, Nothing}=nothing, real_tol::Real=Inf, imag_tol::Real=Inf)
```

Use a dense eigenvalue solver to find the decaying modes of the PSOModel. Each mode consists of an eigenvalue `λ` and a spatial distribution vector `v`. The frequency of the mode is `imag(λ)/(2π)` and the decay rate is `-2*real(λ)/(2π)`. `min_freq` and `max_freq` give the frequency range in which to find eigenvalues. Passivity is enforced using an inverse power method solver, and `real_tol` and `imag_tol` are the tolerances used in that method to determine convergence of the real and imaginary parts of the eigenvalue.
