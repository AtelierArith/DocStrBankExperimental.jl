```
create_flux(lat, lon, mapV::MapV = get_map(emm720);
            Cnb          = repeat(I(3),1,1,length(lat)),
            alt          = 1000,
            dt           = 0.1,
            meas_var     = 1.0^2,
            fogm_sigma   = 1.0,
            fogm_tau     = 600.0,
            silent::Bool = false)
```

Create compensated (clean) vector magnetometer measurements from a vector magnetic anomaly map.

**Arguments:**

  * `lat`:        latitude  [rad]
  * `lon`:        longitude [rad]
  * `mapV`:       (optional) `MapV` vector magnetic anomaly map struct
  * `Cnb`:        (optional) direction cosine matrix (body to navigation) [-]
  * `alt`:        (optional) altitude  [m]
  * `dt`:         (optional) measurement time step [s]
  * `meas_var`:   (optional) measurement (white) noise variance [nT^2]
  * `fogm_sigma`: (optional) FOGM catch-all bias [nT]
  * `fogm_tau`:   (optional) FOGM catch-all time constant [s]
  * `silent`:     (optional) if true, no print outs

**Returns:**

  * `flux`: `MagV` vector magnetometer measurement struct
