```
create_XYZ0(mapS::Union{MapS,MapSd,MapS3D} = get_map(namad);
            alt            = 1000,
            dt             = 0.1,
            t              = 300,
            v              = 68,
            ll1::Tuple     = (),
            ll2::Tuple     = (),
            N_waves::Int   = 1,
            attempts::Int  = 10,
            info::String   = "Simulated data",
            flight         = 1,
            line           = 1,
            year           = 2023,
            doy            = 154,
            mapV::MapV     = get_map(emm720),
            cor_sigma      = 1.0,
            cor_tau        = 600.0,
            cor_var        = 1.0^2,
            cor_drift      = 0.001,
            cor_perm_mag   = 5.0,
            cor_ind_mag    = 5.0,
            cor_eddy_mag   = 0.5,
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
            fogm_sigma     = 1.0,
            baro_tau       = 3600.0,
            acc_tau        = 3600.0,
            gyro_tau       = 3600.0,
            fogm_tau       = 600.0,
            save_h5::Bool  = false,
            xyz_h5::String = "xyz_data.h5",
            silent::Bool   = false)
```

Create basic flight data. Assumes constant altitude (2D flight). No required arguments, though many are available to create custom data.

**Trajectory Arguments:**

  * `mapS`:     (optional) `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `alt`:      (optional) altitude  [m]
  * `dt`:       (optional) measurement time step [s]
  * `t`:        (optional) total flight time, ignored if `ll2` is set [s]
  * `v`:        (optional) approximate aircraft velocity [m/s]
  * `ll1`:      (optional) initial (lat,lon) point [deg]
  * `ll2`:      (optional) final   (lat,lon) point [deg]
  * `N_waves`:  (optional) number of sine waves along path
  * `attempts`: (optional) maximum attempts at creating flight path on `mapS`
  * `info`:     (optional) flight data information
  * `flight`:   (optional) flight number
  * `line`:     (optional) line number, i.e., segment within `flight`
  * `year`:     (optional) year
  * `doy`:      (optional) day of year
  * `mapV`:     (optional) `MapV` vector magnetic anomaly map struct
  * `save_h5`:  (optional) if true, save `xyz` to `xyz_h5`
  * `xyz_h5`:   (optional) path/name of flight data HDF5 file to save (`.h5` extension optional)

**Compensated Measurement Corruption Arguments:**

  * `cor_var`:        (optional) corruption measurement (white) noise variance [nT^2]
  * `fogm_sigma`:     (optional) FOGM catch-all bias [nT]
  * `fogm_tau`:       (optional) FOGM catch-all time constant [s]

**Uncompensated Measurement Corruption Arguments:**

  * `cor_sigma`:      (optional) corruption FOGM catch-all bias [nT]
  * `cor_tau`:        (optional) corruption FOGM catch-all time constant [s]
  * `cor_var`:        (optional) corruption measurement (white) noise variance [nT^2]
  * `cor_drift`:      (optional) corruption measurement linear drift [nT/s]
  * `cor_perm_mag`:   (optional) corruption permanent field TL coef std dev
  * `cor_ind_mag`:    (optional) corruption induced field TL coef std dev
  * `cor_eddy_mag`:   (optional) corruption eddy current TL coef std dev

**INS Arguments:**

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

**General Arguments:**

  * `silent`: (optional) if true, no print outs

**Returns:**

  * `xyz`: `XYZ0` flight data struct
