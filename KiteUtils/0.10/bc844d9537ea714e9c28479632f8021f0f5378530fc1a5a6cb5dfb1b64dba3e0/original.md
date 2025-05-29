```
initial_kite_ref_frame(vec_c, v_app)
```

Calculate the initial orientation of the kite based on the last tether segment and the apparent wind speed.

Parameters:

  * `vec_c`: (`pos_n`-2) - (`pos_n`-1) n: number of particles without the three kite particles                                   that do not belong to the main thether (P1, P2 and P3).
  * `v_app`: vector of the apparent wind speed

Returns: x, y, z:  the unit vectors of the kite reference frame in the ENU reference frame
