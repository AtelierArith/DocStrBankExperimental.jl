```
create_informed_xyz(xyz::XYZ, ind, mapS::Union{MapS,MapSd,MapS3D},
                    use_mag::Symbol, use_vec::Symbol, TL_coef::Vector;
                    terms::Vector{Symbol} = [:permanent,:induced,:eddy],
                    disp_min = 100,
                    disp_max = 500,
                    Bt_disp  = 50,
                    Bt_scale = 50000)
```

Create knowledge-informed data from existing data. Given map information, an `XYZ` structure with magnetometer readings, and a fitted Tolles-Lawson model, this function creates a consistent, displaced `XYZ` structure representing what the `use_mag` and `mag_1_c` would have collected had the entire flight been laterally shifted by (`disp_min`,`disp_max`), assuming that the linear aircraft model is reasonably accurate. It makes use of a Taylor expansion of the map information to update the expected changes due to the alternative map location *and* due to the imputed aircraft field. The aircraft "noise" is then carried over into `use_mag` in the new `XYZ` data.

**Arguments:**

  * `xyz`:      `XYZ` flight data struct
  * `ind`:      selected data indices
  * `mapS`:     `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `use_mag`:  uncompensated scalar magnetometer to use for `y` target vector {`:mag_1_uc`, etc.}
  * `use_vec`:  vector magnetometer (fluxgate) to use for Tolles-Lawson `A` matrix {`:flux_a`, etc.}
  * `TL_coef`:  Tolles-Lawson coefficients
  * `terms`:    (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`}
  * `disp_min`: (optional) minimum trajectory displacement [m]
  * `disp_max`: (optional) maximum trajectory displacement [m]
  * `Bt_disp`:  (optional) target total magnetic field magnitude displacement offset [nT]
  * `Bt_scale`: (optional) scaling factor for induced & eddy current terms [nT]

**Returns:**

  * `xyz_disp`: `XYZ` flight data struct with displaced trajectory & modified magnetometer readings
