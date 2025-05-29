```
(ins::INS)(ind = trues(ins.N);
           err::Real   = 0.0,
           lat::Vector = [zero(ins.lat[ind]);],
           lon::Vector = [zero(ins.lon[ind]);])
```

Get inertial navigation system data at specific indices, possibly zeroed.

**Arguments:**

  * `ins`: `INS` inertial navigation system struct
  * `ind`: (optional) selected data indices
  * `err`: (optional) additional position error [m]
  * `lat`: (optional) initial truth latitude  [rad]
  * `lon`: (optional) initial truth longitude [rad]

**Returns:**

  * `ins`: `INS` inertial navigation system struct at `ind`
