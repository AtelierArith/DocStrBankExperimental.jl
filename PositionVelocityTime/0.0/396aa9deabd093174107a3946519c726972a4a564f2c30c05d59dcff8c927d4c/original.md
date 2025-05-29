Calculates ECEF position of user

```julia
calc_PVT(satellite_states)
calc_PVT(satellite_states, prev_pvt)
calc_PVT(satellite_states, prev_pvt, min_elevation)

```

´sat_state´: satellite state, combining decoded data, code- and carrierphase 

´min*elevation´: The minimum elevation for a satellite, that can be used for a positioning                    Hint: The elevation starts here with 0° at the horizon and has its maximum with 90° in the zenith.                    min*elevation = -100, deactivates the  elevation filter

This function calculates the position of the user in ECEF coordinates       incl. earth rotation correction

The implementation follows IS-GPS-200K Table 20-IV.
