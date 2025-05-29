```julia
struct SemiMarkov{A<:BaytesFilters.SemiMarkovInitiation, B<:BaytesFilters.SemiMarkovTransition, C} <: BaytesFilters.ParticleKernel
```

Semi-Markov Kernel for particle propagation.

# Fields

  * `initial::BaytesFilters.SemiMarkovInitiation`: Initial distribution, function of iter only.
  * `transition::BaytesFilters.SemiMarkovTransition`: Transition distribution, function of full particle trajectory and current iteration count.
  * `evidence::Any`: Data distribution to weight particles. Function of full data, particle trajectory and current iteration count.
