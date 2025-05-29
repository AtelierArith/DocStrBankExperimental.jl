```
force_coefficients(eos, cond)
```

Get coefficients for forces for a specific EOS (component interactions). For most cubics, these are a set of attractive (linear and quadratic) forces and a set of linear repulsive forces.

Note that the current implementation of flash assumes that these are independent of the  compositions themselves.

See also [`force_coefficients!`](@ref)
