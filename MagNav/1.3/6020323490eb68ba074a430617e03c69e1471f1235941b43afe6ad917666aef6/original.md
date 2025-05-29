```
get_Axy(lines, df_line::DataFrame,
        df_flight::DataFrame, df_map::DataFrame,
        features_setup::Vector{Symbol}   = [:mag_1_uc,:TL_A_flux_a];
        features_no_norm::Vector{Symbol} = Symbol[],
        y_type::Symbol     = :d,
        use_mag::Symbol    = :mag_1_uc,
        use_mag_c::Symbol  = :mag_1_c,
        use_vec::Symbol    = :flux_a,
        terms              = [:permanent,:induced,:eddy],
        terms_A            = [:permanent,:induced,:eddy,:bias],
        sub_diurnal::Bool  = false,
        sub_igrf::Bool     = false,
        bpf_mag::Bool      = false,
        reorient_vec::Bool = false,
        l_window::Int      = -1,
        mod_TL::Bool       = false,
        map_TL::Bool       = false,
        return_B::Bool     = false,
        silent::Bool       = true)
```

Get "external" Tolles-Lawson `A` matrix, `x` data matrix, & `y` target vector from multiple flight lines, possibly multiple flights. Optionally return `Bt` & `B_dot` used to create the "external" Tolles-Lawson `A` matrix.

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

  * `features_setup`:   vector of features to include
  * `features_no_norm`: (optional) vector of features to not normalize
  * `y_type`: (optional) `y` target type

      * `:a` = anomaly field  #1, compensated tail stinger total field scalar magnetometer measurements
      * `:b` = anomaly field  #2, interpolated `magnetic anomaly map` values
      * `:c` = aircraft field #1, difference between uncompensated cabin total field scalar magnetometer measurements and interpolated `magnetic anomaly map` values
      * `:d` = aircraft field #2, difference between uncompensated cabin and compensated tail stinger total field scalar magnetometer measurements
      * `:e` = BPF'd total field, bandpass filtered uncompensated cabin total field scalar magnetometer measurements
  * `use_mag`:      (optional) uncompensated scalar magnetometer to use for `y` target vector {`:mag_1_uc`, etc.}, only used for `y_type = :c, :d, :e`
  * `use_mag_c`:    (optional) compensated scalar magnetometer to use for `y` target vector {`:mag_1_c`, etc.}, only used for `y_type = :a, :d`
  * `use_vec`:      (optional) vector magnetometer (fluxgate) to use for "external" Tolles-Lawson `A` matrix {`:flux_a`, etc.}
  * `terms`:        (optional) Tolles-Lawson terms to use for `A` within `x` data matrix {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `terms_A`:      (optional) Tolles-Lawson terms to use for "external" Tolles-Lawson `A` matrix {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `sub_diurnal`:  (optional) if true, subtract diurnal from scalar magnetometer measurements
  * `sub_igrf`:     (optional) if true, subtract IGRF from scalar magnetometer measurements
  * `bpf_mag`:      (optional) if true, bpf scalar magnetometer measurements in `x` data matrix
  * `reorient_vec`: (optional) if true, align vector magnetometer measurements with body frame
  * `l_window`:     (optional) trim data by `N % l_window`, `-1` to ignore
  * `mod_TL`:       (optional) if true, create modified  "external" Tolles-Lawson `A` matrix with `use_mag`
  * `map_TL`:       (optional) if true, create map-based "external" Tolles-Lawson `A` matrix
  * `return_B`:     (optional) if true, also return `Bt` & `B_dot`
  * `silent`:       (optional) if true, no print outs

**Returns:**

  * `A`:        `N` x `N_TL` "external" Tolles-Lawson `A` matrix (`N_TL` is number of Tolles-Lawson coefficients)
  * `x`:        `N` x `Nf` data matrix (`Nf` is number of features)
  * `y`:        length-`N` target vector
  * `no_norm`:  length-`Nf` Boolean indices of features to not be normalized
  * `features`: length-`Nf` feature vector (including components of TL `A`, etc.)
  * `l_segs`:   length-`N_lines` vector of lengths of `lines`, sum(l_segs) = `N`
  * `Bt`:       if `return_B = true`, length-`N` magnitude of total field measurements used to create `A` [nT]
  * `B_dot`:    if `return_B = true`, `N` x `3` finite differences of total field vector used to create `A` [nT]
