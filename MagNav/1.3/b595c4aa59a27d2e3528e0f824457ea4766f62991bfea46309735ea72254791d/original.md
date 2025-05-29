```
get_ins(xyz::XYZ, ind = trues(xyz.traj.N);
        N_zero_ll::Int  = 0,
        t_zero_ll::Real = 0,
        err::Real       = 0.0)
```

Get inertial navigation system data at specific indices, possibly zeroed.

**Arguments:**

  * `xyz`:       `XYZ` flight data struct
  * `ind`:       (optional) selected data indices
  * `N_zero_ll`: (optional) number of samples (instances) to zero INS lat/lon to truth (`xyz.traj`)
  * `t_zero_ll`: (optional) length of time to zero INS lat/lon to truth (`xyz.traj`), overwrites `N_zero_ll`
  * `err`:       (optional) additional position error [m]

**Returns:**

  * `ins`: `INS` inertial navigation system struct at `ind`
