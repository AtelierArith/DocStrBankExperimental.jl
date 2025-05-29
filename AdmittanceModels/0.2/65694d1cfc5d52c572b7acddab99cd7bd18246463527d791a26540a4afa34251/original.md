```
lossless_modes_sparse(pso::PSOModel; num_modes=1, maxiter=200)
```

Use a sparse generalized eigenvalue solver to find the `num_modes` lowest frequency modes of the PSOModel neglecting loss. Each mode consists of an eigenvalue `λ` and an eigenvector `v`. The frequency of the mode is `imag(λ)/(2π)` and the decay rate is `-2*real(λ)/(2π)`.
