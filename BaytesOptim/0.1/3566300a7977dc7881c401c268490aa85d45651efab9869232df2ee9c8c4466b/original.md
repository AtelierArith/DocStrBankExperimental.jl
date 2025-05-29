```julia
struct Optimizer{M<:BaytesOptim.OptimKernel, N<:BaytesOptim.OptimTune} <: BaytesCore.AbstractAlgorithm
```

Stores information for proposal step.

# Fields

  * `kernel::BaytesOptim.OptimKernel`: Optimizer
  * `tune::BaytesOptim.OptimTune`: Tuning configuration for kernel.
