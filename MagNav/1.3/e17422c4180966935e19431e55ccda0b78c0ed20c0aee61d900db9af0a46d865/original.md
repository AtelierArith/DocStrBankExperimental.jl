```
comp_test(comp_params::CompParams, lines,
          df_line::DataFrame, df_flight::DataFrame, df_map::DataFrame;
          temp_params::TempParams = TempParams(),
          silent::Bool            = false)
```

Evaluate performance of an aeromagnetic compensation model.

**Arguments:**

  * `comp_params`: `CompParams` aeromagnetic compensation parameters struct, either:

      * `NNCompParams`:  neural network-based aeromagnetic compensation parameters struct
      * `LinCompParams`: linear aeromagnetic compensation parameters struct
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

  * `df_map`: lookup table (DataFrame) of map data files

| **Field**  | **Type** | **Description**                                                             |
|:---------- |:-------- |:--------------------------------------------------------------------------- |
| `map_name` | `Symbol` | name of magnetic anomaly map                                                |
| `map_file` | `String` | path/name of map data HDF5 or MAT file (`.h5` or `.mat` extension required) |

  * `temp_params`: (optional) `TempParams` temporary temporal parameters struct
  * `silent`:      (optional) if true, no print outs

**Returns:**

  * `y`:        length-`N` target vector
  * `y_hat`:    length-`N` prediction vector
  * `err`:      length-`N` mean-corrected (per line) compensation error
  * `features`: length-`Nf` feature vector (including components of TL `A`, etc.)
