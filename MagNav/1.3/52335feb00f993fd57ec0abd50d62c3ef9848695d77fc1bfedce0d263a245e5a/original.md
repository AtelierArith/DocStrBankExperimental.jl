```
create_flux(path::Path, mapV::MapV = get_map(emm720);
            meas_var     = 1.0^2,
            fogm_sigma   = 1.0,
            fogm_tau     = 600.0,
            silent::Bool = false)
```

Create compensated (clean) vector magnetometer measurements from a vector magnetic anomaly map.

**Arguments:**

  * `path`:       `Path` struct, i.e., `Traj` trajectory struct, `INS` inertial navigation system struct, or `FILTout` filter extracted output struct
  * `mapV`:       (optional) `MapV` vector magnetic anomaly map struct
  * `meas_var`:   (optional) measurement (white) noise variance [nT^2]
  * `fogm_sigma`: (optional) FOGM catch-all bias [nT]
  * `fogm_tau`:   (optional) FOGM catch-all time constant [s]
  * `silent`:     (optional) if true, no print outs

**Returns:**

  * `flux`: `MagV` vector magnetometer measurement struct
