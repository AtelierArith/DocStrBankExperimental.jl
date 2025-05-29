Ridge regularization.

# Constructor

```
SemRidge(;α_ridge, which_ridge, nparams, parameter_type = Float64, implied = nothing, kwargs...)
```

# Arguments

  * `α_ridge`: hyperparameter for penalty term
  * `which_ridge::Vector`: Vector of parameter labels (Symbols) or indices that indicate which parameters should be regularized.
  * `nparams::Int`: number of parameters of the model
  * `implied::SemImplied`: implied part of the model
  * `parameter_type`: type of the parameters

# Examples

```julia
my_ridge = SemRidge(;α_ridge = 0.02, which_ridge = [:λ₁, :λ₂, :ω₂₃], nparams = 30, implied = my_implied)
```

# Interfaces

Analytic gradients and hessians are available.
