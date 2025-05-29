```
get_x(lines, df_line::DataFrame, df_flight::DataFrame,
      features_setup::Vector{Symbol}   = [:mag_1_uc,:TL_A_flux_a];
      features_no_norm::Vector{Symbol} = Symbol[],
      terms              = [:permanent,:induced,:eddy],
      sub_diurnal::Bool  = false,
      sub_igrf::Bool     = false,
      bpf_mag::Bool      = false,
      reorient_vec::Bool = false,
      l_window::Int      = -1,
      silent::Bool       = true)
```

Get `x` data matrix from multiple flight lines, possibly multiple flights.

**Arguments:**

  * `lines`:   selected line number(s)
  * `df_line`: lookup table (DataFrame) of `lines`

| **Field**  | **Type** | **Description**                                            |
|:---------- |:-------- |:---------------------------------------------------------- |
| `flight`   | `Symbol` | flight name (e.g., `:Flt1001`)                             |
| `line`     | `Real`   | line number, i.e., segments within `flight`                |
| `t_start`  | `Real`   | start time of `line` to use [s]                            |
| `t_end`    | `Real`   | end   time of `line` to use [s]                            |
| `map_name` | `Symbol` | (optional) name of magnetic anomaly map relevant to `line` |

  * `df_flight`: lookup table (DataFrame) of flight data files

| **Field**  | **Type** | **Description**                                                                                               |
|:---------- |:-------- |:------------------------------------------------------------------------------------------------------------- |
| `flight`   | `Symbol` | flight name (e.g., `:Flt1001`)                                                                                |
| `xyz_type` | `Symbol` | subtype of `XYZ` to use for flight data {`:XYZ0`,`:XYZ1`,`:XYZ20`,`:XYZ21`}                                   |
| `xyz_set`  | `Real`   | flight dataset number (used to prevent improper mixing of datasets, such as different magnetometer locations) |
| `xyz_file` | `String` | path/name of flight data CSV, HDF5, or MAT file (`.csv`, `.h5`, or `.mat` extension required)                 |

  * `features_setup`:   vector of features to include
  * `features_no_norm`: (optional) vector of features to not normalize
  * `terms`:            (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `sub_diurnal`:      (optional) if true, subtract diurnal from scalar magnetometer measurements
  * `sub_igrf`:         (optional) if true, subtract IGRF from scalar magnetometer measurements
  * `bpf_mag`:          (optional) if true, bpf scalar magnetometer measurements
  * `reorient_vec`:     (optional) if true, align vector magnetometer measurements with body frame
  * `l_window`:         (optional) trim data by `N % l_window`, `-1` to ignore
  * `silent`:           (optional) if true, no print outs

**Returns:**

  * `x`:        `N` x `Nf` data matrix (`Nf` is number of features)
  * `no_norm`:  length-`Nf` Boolean indices of features to not be normalized
  * `features`: length-`Nf` feature vector (including components of TL `A`, etc.)
  * `l_segs`:   length-`N_lines` vector of lengths of `lines`, sum(l_segs) = `N`
