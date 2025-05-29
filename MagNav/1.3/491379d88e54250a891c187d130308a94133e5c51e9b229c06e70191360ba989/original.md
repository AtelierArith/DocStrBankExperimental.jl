```
comp_m3_test(comp_params::NNCompParams, lines,
             df_line::DataFrame, df_flight::DataFrame, df_map::DataFrame;
             temp_params::TempParams = TempParams(),
             silent::Bool            = false)
```

Evaluate performance of neural network-based aeromagnetic compensation, model 3 with additional outputs for explainability.

**Arguments:**

  * `comp_params`: `NNCompParams` neural network-based aeromagnetic compensation parameters struct
  * `lines`:       selected line number(s)
  * `df_line`:     lookup table (DataFrame) of `lines`

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

  * `df_map`: lookup table (DataFrame) of map data files

| **Field**  | **Type** | **Description**                                                             |
|:---------- |:-------- |:--------------------------------------------------------------------------- |
| `map_name` | `Symbol` | name of magnetic anomaly map                                                |
| `map_file` | `String` | path/name of map data HDF5 or MAT file (`.h5` or `.mat` extension required) |

  * `temp_params`: (optional) `TempParams` temporary temporal parameters struct
  * `silent`:      (optional) if true, no print outs

**Returns:**

  * `TL_perm`:      `3` x `N` matrix of TL permanent vector field
  * `TL_induced`:   `3` x `N` matrix of TL induced vector field
  * `TL_eddy`:      `3` x `N` matrix of TL eddy current vector field
  * `TL_aircraft`:  `3` x `N` matrix of TL aircraft vector field
  * `B_unit`:       `3` x `N` matrix of normalized vector magnetometer measurements
  * `B_vec`:        `3` x `N` matrix of vector magnetometer measurements
  * `y_nn`:         `3` x `N` matrix of vector neural network correction (for scalar models, in direction of `Bt`)
  * `vec_aircraft`: `3` x `N` matrix of predicted aircraft vector field
  * `y`:            length-`N` target vector
  * `y_hat`:        length-`N` prediction vector
  * `err`:          length-`N` mean-corrected (per line) compensation error
  * `features`:     length-`Nf` feature vector (including components of TL `A`, etc.)
