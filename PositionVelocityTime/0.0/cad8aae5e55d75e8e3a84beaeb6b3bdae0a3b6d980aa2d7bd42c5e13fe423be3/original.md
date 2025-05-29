```
Calculates ECI Position by converting ECEF position
```

```julia
sat_position_rotation(sat_state, dt)

```

```
´sat_state´: satellite state, combining decoded data, code- and carrierphase 


This function calculates the position of the SV in ECEF coorinates and
converts this position into ECI coordinates.
The implementation follows IS-GPS-200K
```
