```
EopIau2000A{T}
```

Earth orientation parameters for the model IAU 2000A.

!!! note
    Each field will be an `AbstractInterpolation` indexed by the Julian Day.  Hence, if one want to obtain, for example, the X component of the polar motion with respect to the crust at 19 June 2018, the following can be used:

    ```
    x[DateTime(2018, 6, 19, 0, 0, 0) |> datetime2julian]
    ```


# Fields

  * `x, y`: Polar motion with respect to the crust [arcsec].
  * `Δut1_utc`: Irregularities of the rotation angle [s].
  * `lod`: Length of day offset [ms].
  * `δx, δy`: Celestial pole offsets referred to the model IAU2000A [milliarcsec].
  * `*_error`: Errors in the components [same unit as the component].
