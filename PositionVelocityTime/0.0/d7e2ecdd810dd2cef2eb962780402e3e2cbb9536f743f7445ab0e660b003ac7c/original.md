```
Calculates ECEF Position of SV
```

```julia
sat_position_ECEF(sat_state)

```

```
´sat_state´: satellite state, combining decoded data, code- and carrierphase 


This function calculates the position of the SV in ECEF coorinates.
The implementation follows IS-GPS-200K Table 20-IV.
```
