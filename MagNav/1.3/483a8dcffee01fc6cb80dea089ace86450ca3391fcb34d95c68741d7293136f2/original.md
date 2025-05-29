```
get_y(xyz::XYZ, ind = trues(xyz.traj.N),
      map_val           = -1);
      y_type::Symbol    = :d,
      use_mag::Symbol   = :mag_1_uc,
      use_mag_c::Symbol = :mag_1_c,
      sub_diurnal::Bool = false,
      sub_igrf::Bool    = false)
```

Get `y` target vector.

**Arguments:**

  * `xyz`:     `XYZ` flight data struct
  * `ind`:     selected data indices
  * `map_val`: (optional) scalar magnetic anomaly map values, only used for `y_type = :b`
  * `y_type`:  (optional) `y` target type

      * `:a` = anomaly field  #1, compensated tail stinger total field scalar magnetometer measurements
      * `:b` = anomaly field  #2, interpolated `magnetic anomaly map` values
      * `:c` = aircraft field #1, difference between uncompensated cabin total field scalar magnetometer measurements and interpolated `magnetic anomaly map` values
      * `:d` = aircraft field #2, difference between uncompensated cabin and compensated tail stinger total field scalar magnetometer measurements
      * `:e` = BPF'd total field, bandpass filtered uncompensated cabin total field scalar magnetometer measurements
  * `use_mag`:     (optional) uncompensated scalar magnetometer to use for `y` target vector {`:mag_1_uc`, etc.}, only used for `y_type = :c, :d, :e`
  * `use_mag_c`:   (optional) compensated scalar magnetometer to use for `y` target vector {`:mag_1_c`, etc.}, only used for `y_type = :a, :d`
  * `sub_diurnal`: (optional) if true, subtract diurnal from scalar magnetometer measurements
  * `sub_igrf`:    (optional) if true, subtract IGRF from scalar magnetometer measurements

**Returns:**

  * `y`: length-`N` target vector
