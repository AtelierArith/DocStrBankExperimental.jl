```
phase_space_integrand(function_σs, ms; k::Int)
```

Calculate the phase space integrand for a given function `function_σs`, and mass tuple `ms`. The key argument `k` specifies the mapping: `σk->[0,1]`, zk->[0,1]. It returns an integrand function of x, x ∈ [0,1]x[0,1] domain to pass to a numerical integrator.

# Arguments

  * `function_σs`: A function that takes a MandelstamTuple and returns a scalar.
  * `ms`: A scalar representing the mass.
  * `k`: An integer representing the mapping index.

# Usage

```julia
integrand = phase_space_integrand(function_σs, ms; k)
```

# See also

  * `x2σs`
  * `projection_integrand`
