```julia
struct Markov{A, B, C} <: BaytesFilters.ParticleKernel
```

Markov Kernel for particle propagation.

# Fields

  * `initial::Any`: Initial distribution, function of iter only.
  * `transition::Any`: Transition distribution, function of full particle trajectory and current iteration count.
  * `evidence::Any`: Data distribution to weight particles. Function of full data, particle trajectory and current iteration count.
