```
UniformStokesDrift(; ∂z_uˢ=zerofunction, ∂z_vˢ=zerofunction, ∂t_uˢ=zerofunction, ∂t_vˢ=zerofunction, parameters=nothing)
```

Construct a set of functions for a Stokes drift velocity field corresponding to a horizontally-uniform surface gravity wave field, with optional `parameters`.

If `parameters=nothing`, then the functions `∂z_uˢ`, `∂z_vˢ`, `∂t_uˢ`, `∂t_vˢ` must be callable with signature `(z, t)`. If `!isnothing(parameters)`, then functions must be callable with the signature `(z, t, parameters)`.

To resolve the evolution of the Lagrangian-mean momentum, we require vertical-derivatives and time-derivatives of the horizontal components of the Stokes drift, `uˢ` and `vˢ`.

# Examples

Exponentially decaying Stokes drift corresponding to a surface Stokes drift of `uˢ(z=0) = 0.005` and decay scale `h = 20`:

```jldoctest
using Oceananigans

@inline uniform_stokes_shear(z, t) = 0.005 * exp(z / 20)

stokes_drift = UniformStokesDrift(∂z_uˢ=uniform_stokes_shear)

# output

UniformStokesDrift{Nothing}:
├── ∂z_uˢ: uniform_stokes_shear
├── ∂z_vˢ: zerofunction
├── ∂t_uˢ: zerofunction
└── ∂t_vˢ: zerofunction
```

Exponentially-decaying Stokes drift corresponding to a surface Stokes drift of `uˢ = 0.005` and decay scale `h = 20`, using parameters:

```jldoctest
using Oceananigans

@inline uniform_stokes_shear(z, t, p) = p.uˢ * exp(z / p.h)

stokes_drift_parameters = (uˢ = 0.005, h = 20)
stokes_drift = UniformStokesDrift(∂z_uˢ=uniform_stokes_shear, parameters=stokes_drift_parameters)

# output

UniformStokesDrift with parameters (uˢ=0.005, h=20):
├── ∂z_uˢ: uniform_stokes_shear
├── ∂z_vˢ: zerofunction
├── ∂t_uˢ: zerofunction
└── ∂t_vˢ: zerofunction
```
