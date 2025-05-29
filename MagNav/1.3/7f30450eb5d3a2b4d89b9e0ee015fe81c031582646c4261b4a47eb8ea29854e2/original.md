```
create_ins(traj::Traj;
           init_pos_sigma = 3.0,
           init_alt_sigma = 0.001,
           init_vel_sigma = 0.01,
           init_att_sigma = deg2rad(0.01),
           VRW_sigma      = 0.000238,
           ARW_sigma      = 0.000000581,
           baro_sigma     = 1.0,
           ha_sigma       = 0.001,
           a_hat_sigma    = 0.01,
           acc_sigma      = 0.000245,
           gyro_sigma     = 0.00000000727,
           baro_tau       = 3600.0,
           acc_tau        = 3600.0,
           gyro_tau       = 3600.0,
           save_h5::Bool  = false,
           ins_h5::String = "ins_data.h5")
```

Creates an INS trajectory about a true trajectory. Propagates a 17-state Pinson error model to create INS errors.

**Arguments:**

  * `traj`:           `Traj` trajectory struct
  * `init_pos_sigma`: (optional) initial position uncertainty [m]
  * `init_alt_sigma`: (optional) initial altitude uncertainty [m]
  * `init_vel_sigma`: (optional) initial velocity uncertainty [m/s]
  * `init_att_sigma`: (optional) initial attitude uncertainty [rad]
  * `VRW_sigma`:      (optional) velocity random walk [m/s^2 /sqrt(Hz)]
  * `ARW_sigma`:      (optional) angular  random walk [rad/s /sqrt(Hz)]
  * `baro_sigma`:     (optional) barometer bias [m]
  * `ha_sigma`:       (optional) barometer aiding altitude bias [m]
  * `a_hat_sigma`:    (optional) barometer aiding vertical accel bias [m/s^2]
  * `acc_sigma`:      (optional) accelerometer bias [m/s^2]
  * `gyro_sigma`:     (optional) gyroscope bias [rad/s]
  * `baro_tau`:       (optional) barometer time constant [s]
  * `acc_tau`:        (optional) accelerometer time constant [s]
  * `gyro_tau`:       (optional) gyroscope time constant [s]
  * `save_h5`:        (optional) if true, save `ins` to `ins_h5`
  * `ins_h5`:         (optional) path/name of INS data HDF5 file to save (`.h5` extension optional)

**Returns:**

  * `ins`: `INS` inertial navigation system struct
