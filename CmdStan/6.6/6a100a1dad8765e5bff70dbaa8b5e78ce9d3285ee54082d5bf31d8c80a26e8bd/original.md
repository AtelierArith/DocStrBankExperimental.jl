# Variational type and constructor

Settings for method=Variational() in Stanmodel. 

### Method

```julia
Variational(;
  grad_samples=1,
  elbo_samples=100,
  eta_adagrad=0.1,
  iter=10000,
  tol_rel_obj=0.01,
  eval_elbo=100,
  algorithm=:meanfield,          
  output_samples=10000
)
```

### Optional arguments

```julia
* `algorithm::Symbol`             : Variational inference algorithm
                                  : meanfield
                                  : fullrank
* `iter::Int64`                   : Maximum number of iterations
* `grad_samples::Int`             : No of samples for MC estimate of gradients
* `elbo_samples::Int`             : No of samples for MC estimate of ELBO
* `eta::Float64`                  : Step size weighting parameter for adaptive sequence
* `adapt::Adapt`                  : Warmup adaptations
* `tol_rel_obj::Float64`          : Tolerance on the relative norm of objective
* `eval_elbo::Int`                : Tolerance on the relative norm of objective
* `output_samples::Int`           : Number of posterior samples to draw and save
```

### Related help

```julia
?Stanmodel                        : Create a StanModel
?Stan.Method                      : Available top level methods
?Stan.Adapt                       : Adaptation settings
```
