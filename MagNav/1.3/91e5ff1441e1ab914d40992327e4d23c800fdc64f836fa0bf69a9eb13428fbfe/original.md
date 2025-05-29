```
create_P0(lat1 = deg2rad(45);
          init_pos_sigma   = 3.0,
          init_alt_sigma   = 0.001,
          init_vel_sigma   = 0.01,
          init_att_sigma   = deg2rad(0.01),
          ha_sigma         = 0.001,
          a_hat_sigma      = 0.01,
          acc_sigma        = 0.000245,
          gyro_sigma       = 0.00000000727,
          fogm_sigma       = 3.0,
          vec_sigma        = 1000.0,
          vec_states::Bool = false,
          fogm_state::Bool = true,
          P0_TL            = [])
```

Create initial covariance matrix `P0`.

**Arguments:**

  * `lat1`:           initial approximate latitude [rad]
  * `init_pos_sigma`: (optional) initial position uncertainty [m]
  * `init_alt_sigma`: (optional) initial altitude uncertainty [m]
  * `init_vel_sigma`: (optional) initial velocity uncertainty [m/s]
  * `init_att_sigma`: (optional) initial attitude uncertainty [rad]
  * `ha_sigma`:       (optional) barometer aiding altitude bias [m]
  * `a_hat_sigma`:    (optional) barometer aiding vertical accel bias [m/s^2]
  * `acc_sigma`:      (optional) accelerometer bias [m/s^2]
  * `gyro_sigma`:     (optional) gyroscope bias [rad/s]
  * `fogm_sigma`:     (optional) FOGM catch-all bias [nT]
  * `vec_sigma`:      (optional) vector magnetometer noise std dev
  * `vec_states`:     (optional) if true, include vector magnetometer states
  * `fogm_state`:     (optional) if true, include FOGM catch-all bias state
  * `P0_TL`:          (optional) initial Tolles-Lawson covariance matrix

**Returns:**

  * `P0`: initial covariance matrix
