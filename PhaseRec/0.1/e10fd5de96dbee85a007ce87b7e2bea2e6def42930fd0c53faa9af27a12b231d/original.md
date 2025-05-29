```
phaserec(s2ft, size; radius = 0.6, maxstep = 300, ϵ = 10^-5[, noise])
```

Reconstruct an image from the two-point correlation function. `s2ft` is unnormalized two-point correlation function in frequency domain and `size` are dimensions of the original image. Optional parameter `radius` governs noise filtration. `maxsteps` is a maximal number of iterations. Smaller `ϵ` usually produces better results, but default value should be OK for all cases. `noise` is an optional array of booleans which contains initial approximation.

# References

1. A. Cherkasov, A. Ananev, Adaptive phase-retrieval stochastic reconstruction with correlation functions: Three-dimensional images from two-dimensional cuts, Phys. Rev. E, 104, 3, 2021

See also: [`two_point`](@ref).
