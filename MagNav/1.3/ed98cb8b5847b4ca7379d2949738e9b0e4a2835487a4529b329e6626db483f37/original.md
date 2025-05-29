```
create_traj(mapS::Union{MapS,MapSd,MapS3D} = get_map(namad);
            alt             = 1000,
            dt              = 0.1,
            t               = 300,
            v               = 68,
            ll1::Tuple      = (),
            ll2::Tuple      = (),
            N_waves::Int    = 1,
            attempts::Int   = 10,
            save_h5::Bool   = false,
            traj_h5::String = "traj_data.h5")
```

Create `Traj` trajectory struct with a straight or sinusoidal flight path at constant altitude (2D flight).

**Arguments:**

  * `mapS`:     (optional) `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `alt`:      (optional) altitude  [m]
  * `dt`:       (optional) measurement time step [s]
  * `t`:        (optional) total flight time, ignored if `ll2` is set [s]
  * `v`:        (optional) approximate aircraft velocity [m/s]
  * `ll1`:      (optional) initial (lat,lon) point [deg]
  * `ll2`:      (optional) final   (lat,lon) point [deg]
  * `N_waves`:  (optional) number of sine waves along path
  * `attempts`: (optional) maximum attempts at creating flight path on `mapS`
  * `save_h5`:  (optional) if true, save `traj` to `traj_h5`
  * `traj_h5`:  (optional) path/name of trajectory data HDF5 file to save (`.h5` extension optional)

**Returns:**

  * `traj`: `Traj` trajectory struct
