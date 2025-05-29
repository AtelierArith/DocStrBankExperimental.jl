```
StaticSmagorinskyModel(; kwargs...)
```

Subgrid-scale advective transport of resolved momentum, approximated with the static Smagorinsky model.

# Keywords

  * `Cs = 0.1`: The Smagorinsky coefficient $C_\mathrm{S}$.
  * `dealiasing`: The level of dealiasing, determining the physical-domain resolution at nonlinear operations are performed. The default `nothing` gives a physical-domain resolution that matches the frequency-domain resolution (rounded up to an even value). Alternatively, `dealiasing` can be set to `:quadratic` for a resolution based on the “3/2-rule” or to a tuple of two integers to set the resolution manually. Aliasing errors should be reduced for larger resolutions but they can be expected at any resolution.
  * `wall_damping = true`: Adjust the Smagorinsky lenghtscale towards the expected value of $κ x₃$ towards the wall.
  * `wall_damping_exponent = 2`: Exponent of the near-wall adjustment.
