```
volume(model::EoSModel, p, T, z=SA[1.0]; phase=:unknown, threaded=true, vol0=nothing)
```

Calculates the volume (m³) of the compound modelled by `model` at a certain pressure, temperature and moles. `phase` is a Symbol that determines the initial volume root to look for:

  * If `phase =:unknown` (Default), it will return the physically correct volume root with the least gibbs energy.
  * If `phase =:liquid`, it will return the volume of the phase using a liquid initial point.
  * If `phase =:vapor`, it will return the volume of the phase using a gas initial point.
  * If `phase =:solid`, it will return the volume of the phase using a solid initial point (only supported for EoS that support a solid phase)
  * If `phase =:stable`, it will return the physically correct volume root with the least gibbs energy, and perform a stability test on the result.

All volume calculations are checked for mechanical stability, that is: `dP/dV <= 0`.

The calculation of both volume roots can be calculated in serial (`threaded=false`) or in parallel (`threaded=true`).

An initial estimate of the volume `vol0` can be optionally be provided.

!!! tip
    The volume computation may fail and return `NaN` because the default initial point is too far from the actual volume. Providing a value for `vol0` may help in these situations. Such a starting point can be found from physical knowledge, or by computing the volume using a different model for example.


!!! warning "Stability checks"
    The stability check is disabled by default. that means that the volume obtained just follows the the relation `P = pressure(model,V,T,z)`. For single component models, this is alright, but phase splits (with different compositions that the input) can and will occur, meaning that the volume solution does not correspond to an existing phase. For unknown multicomponent mixtures, it is recommended to use a phase equilibrium procedure (like `tp_flash`) to obtain a list of valid compositions, and then perform a volume calculation over those compositions. You can also pass `phase=:stable` to perform the stability test inside the volume solver. Finally, you can perform the stability test after the volume solver:

    ```julia
    v = volume(model,p,T,z)
    isstable(model,v,T,z)
    ```

