```
get_y(lines, df_line::DataFrame, df_flight::DataFrame,
      df_map::DataFrame;
      y_type::Symbol    = :d,
      use_mag::Symbol   = :mag_1_uc,
      use_mag_c::Symbol = :mag_1_c,
      sub_diurnal::Bool = false,
      sub_igrf::Bool    = false,
      l_window::Int     = -1,
      silent::Bool      = true)
```

Get `y` target vector from multiple flight lines, possibly multiple flights.

**Arguments:**

  * `lines`:   selected line number(s)
  * `df_line`: lookup table (DataFrame) of `lines`

| **Field**  | **Type** | **Description**                                                                             |
|:---------- |:-------- |:------------------------------------------------------------------------------------------- |
| `flight`   | `Symbol` | flight name (e.g., `:Flt1001`)                                                              |
| `line`     | `Real`   | line number, i.e., segments within `flight`                                                 |
| `t_start`  | `Real`   | start time of `line` to use [s]                                                             |
| `t_end`    | `Real`   | end   time of `line` to use [s]                                                             |
| `map_name` | `Symbol` | (optional) name of magnetic anomaly map relevant to `line`, only used for `y_type = :b, :c` |

  * `df_flight`: lookup table (DataFrame) of flight data files

| **Field**  | **Type** | **Description**                                                                                               |
|:---------- |:-------- |:------------------------------------------------------------------------------------------------------------- |
| `flight`   | `Symbol` | flight name (e.g., `:Flt1001`)                                                                                |
| `xyz_type` | `Symbol` | subtype of `XYZ` to use for flight data {`:XYZ0`,`:XYZ1`,`:XYZ20`,`:XYZ21`}                                   |
| `xyz_set`  | `Real`   | flight dataset number (used to prevent improper mixing of datasets, such as different magnetometer locations) |
| `xyz_file` | `String` | path/name of flight data CSV, HDF5, or MAT file (`.csv`, `.h5`, or `.mat` extension required)                 |

  * `df_map`: lookup table (DataFrame) of map data files

| **Field**  | **Type** | **Description**                                                             |
|:---------- |:-------- |:--------------------------------------------------------------------------- |
| `map_name` | `Symbol` | name of magnetic anomaly map                                                |
| `map_file` | `String` | path/name of map data HDF5 or MAT file (`.h5` or `.mat` extension required) |

  * `y_type`: (optional) `y` target type

      * `:a` = anomaly field  #1, compensated tail stinger total field scalar magnetometer measurements
      * `:b` = anomaly field  #2, interpolated `magnetic anomaly map` values
      * `:c` = aircraft field #1, difference between uncompensated cabin total field scalar magnetometer measurements and interpolated `magnetic anomaly map` values
      * `:d` = aircraft field #2, difference between uncompensated cabin and compensated tail stinger total field scalar magnetometer measurements
      * `:e` = BPF'd total field, bandpass filtered uncompensated cabin total field scalar magnetometer measurements
  * `use_mag`:     (optional) uncompensated scalar magnetometer to use for `y` target vector {`:mag_1_uc`, etc.}, only used for `y_type = :c, :d, :e`
  * `use_mag_c`:   (optional) compensated scalar magnetometer to use for `y` target vector {`:mag_1_c`, etc.}, only used for `y_type = :a, :d`
  * `sub_diurnal`: (optional) if true, subtract diurnal from scalar magnetometer measurements
  * `sub_igrf`:    (optional) if true, subtract IGRF from scalar magnetometer measurements
  * `l_window`:    (optional) trim data by `N % l_window`, `-1` to ignore
  * `silent`:      (optional) if true, no print outs

**Returns:**

  * `y`: length-`N` target vector
