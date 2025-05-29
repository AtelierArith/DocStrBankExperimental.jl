```
update_exogenous!(ls::RigidBodyMotion,a_edof::AbstractVector)
```

Mutates the exogenous buffer of `ls` with the supplied vector of exogenous accelerations `a_edof`. This function is useful for supplying time-varying exogenous values to the integrator from an outer loop.
