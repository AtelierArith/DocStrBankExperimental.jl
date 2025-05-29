```
sixdof!(ds, s, params, time)
```

dynamic and kinematic ODEs.  Follows format used in DifferentialEquations package.

  * s = x, y, z, phi, theta, psi, u, v, w, p, q, r (same order as State)
  * params = control, massproperties, reference, aeromodel, propmodel, inertialmodel, atmmodel
