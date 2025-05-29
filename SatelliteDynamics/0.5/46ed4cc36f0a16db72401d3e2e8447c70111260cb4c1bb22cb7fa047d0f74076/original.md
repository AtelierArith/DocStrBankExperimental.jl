Module-wide global GravityModel object. This data object is used as the default spherical harmonic gravity field unless one is otherwise provided.

This value can be overridden in your own code as follows:

```julia
SatelliteDynamics.GravityModel = GravityModel(PATH_TO_YOUR_GRAVITY_MODEL)
```

This global variable defaults to use the module's internal version of the EGM2008 model truncated to order and degree 90, if it is not otherwise set.
