```
Calculates ECEF Position by converting ECI position
```

```julia
sat_position_ECI_2_ECEF(sat_state)

```

```
´sat_state´: satellite state, combining decoded data, code- and carrierphase 


This function calculates the position of the SV in ECI coorinates and
converts this position into ECEF coordinates.
The implementation follows IS-GPS-200K
```
