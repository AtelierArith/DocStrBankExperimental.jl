Constant loss term. Can be used for comparability to other packages.

# Constructor

```
SemConstant(;constant_loss, kwargs...)
```

# Arguments

  * `constant_loss::Number`: constant to add to the objective

# Examples

```julia
    my_constant = SemConstant(constant_loss = 42.0)
```

# Interfaces

Analytic gradients and hessians are available.
