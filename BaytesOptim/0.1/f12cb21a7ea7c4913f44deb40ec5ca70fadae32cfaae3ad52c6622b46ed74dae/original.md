```julia
struct OptimDefault{T<:NamedTuple, G, I<:ModelWrappers.AbstractInitialization, U<:BaytesCore.UpdateBool}
```

Default arguments for Optim constructor.

# Fields

  * `kernel::NamedTuple`: Tuning Arguments for individual Optimizer
  * `GradientBackend::Any`: Gradient backend used in Optimization step. Not used if Metropolis sampler is chosen.
  * `init::ModelWrappers.AbstractInitialization`: Method to obtain initial Modelparameter, see 'AbstractInitialization'.
  * `generated::BaytesCore.UpdateBool`: Boolean if generate(_rng, objective) for corresponding model is stored in Optimization Diagnostics.
