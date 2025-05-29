```
eval_filt(traj::Traj, ins::INS, filt_res::FILTres)
```

Extract filter results.

**Arguments:**

  * `traj`:     `Traj` trajectory struct
  * `ins`:      `INS` inertial navigation system struct
  * `filt_res`: `FILTres` filter results struct

**Returns:**

  * `filt_out`: `FILTout` filter extracted output struct
