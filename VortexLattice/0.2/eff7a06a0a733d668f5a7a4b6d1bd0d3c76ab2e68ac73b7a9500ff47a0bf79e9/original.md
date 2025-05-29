```
body_derivatives(system, surfaces, reference, freestream; kwargs...)
```

Returns the derivatives of the body forces and moments with respect to the freestream velocity components `(u, v, w)` and the angular velocity components `(p, q, r)` in the body frame.

The derivatives are returned as two named tuples: `dCF, dCM`

Note that the derivatives with respect to the freestream variables of the panel forces must have been previously computed and stored in `system`

# Arguments:

  * `system`: Object of type `System` which holds system properties
