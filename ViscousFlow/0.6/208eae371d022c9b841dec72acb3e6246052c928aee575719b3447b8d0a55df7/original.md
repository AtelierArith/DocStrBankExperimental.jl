```
force(sol,sys,bodyi[;axes=0,reference_body=bodyi]) -> Tuple{Vector}
```

Calculate the moment and force exerted by the fluid on body `bodyi` from the computational solution `sol` of system `sys`. It returns the force history as a tuple of arrays: one array for each component. If `axes=0` (the default), then the components are provided in the inertial coordinate system. However, this can be changed to any body ID to provide the components in another system. The keyword `force_reference` determines which body's system the moment is taken about. By default, it is the body `bodyi` itself, but any other body can be specified, or the inertial system (by specifying 0).
