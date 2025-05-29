```
create_mag_c(lat, lon, mapS::Union{MapS,MapSd,MapS3D} = get_map(namad);
             alt          = 1000,
             dt           = 0.1,
             meas_var     = 1.0^2,
             fogm_sigma   = 1.0,
             fogm_tau     = 600.0,
             silent::Bool = false)
```

Create compensated (clean) scalar magnetometer measurements from a scalar magnetic anomaly map.

**Arguments:**

  * `lat`:        latitude  [rad]
  * `lon`:        longitude [rad]
  * `mapS`:       (optional) `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `alt`:        (optional) altitude  [m]
  * `dt`:         (optional) measurement time step [s]
  * `meas_var`:   (optional) measurement (white) noise variance [nT^2]
  * `fogm_sigma`: (optional) FOGM catch-all bias [nT]
  * `fogm_tau`:   (optional) FOGM catch-all time constant [s]
  * `silent`:     (optional) if true, no print outs

**Returns:**

  * `mag_c`: compensated (clean) scalar magnetometer measurements [nT]
