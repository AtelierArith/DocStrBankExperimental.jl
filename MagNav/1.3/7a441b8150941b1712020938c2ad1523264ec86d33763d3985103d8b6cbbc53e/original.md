```
create_Qd(dt = 0.1;
          VRW_sigma        = 0.000238,
          ARW_sigma        = 0.000000581,
          baro_sigma       = 1.0,
          acc_sigma        = 0.000245,
          gyro_sigma       = 0.00000000727,
          fogm_sigma       = 3.0,
          vec_sigma        = 1000.0,
          TL_sigma         = [],
          baro_tau         = 3600.0,
          acc_tau          = 3600.0,
          gyro_tau         = 3600.0,
          fogm_tau         = 600.0,
          vec_states::Bool = false,
          fogm_state::Bool = true)
```

Create the discrete time process/system noise matrix `Qd`.

**Arguments:**

  * `dt`:         measurement time step [s]
  * `VRW_sigma`:  (optional) velocity random walk [m/s^2 /sqrt(Hz)]
  * `ARW_sigma`:  (optional) angular  random walk [rad/s /sqrt(Hz)]
  * `baro_sigma`: (optional) barometer bias [m]
  * `acc_sigma`:  (optional) accelerometer bias [m/s^2]
  * `gyro_sigma`: (optional) gyroscope bias [rad/s]
  * `fogm_sigma`: (optional) FOGM catch-all bias [nT]
  * `vec_sigma`:  (optional) vector magnetometer noise std dev
  * `TL_sigma`:   (optional) Tolles-Lawson coefficients estimate std dev
  * `baro_tau`:   (optional) barometer time constant [s]
  * `acc_tau`:    (optional) accelerometer time constant [s]
  * `gyro_tau`:   (optional) gyroscope time constant [s]
  * `fogm_tau`:   (optional) FOGM catch-all time constant [s]
  * `vec_states`: (optional) if true, include vector magnetometer states
  * `fogm_state`: (optional) if true, include FOGM catch-all bias state

**Returns:**

  * `Qd`: discrete time process/system noise matrix
