```
get_ind(xyz::XYZ, line::Real, df_line::DataFrame;
        splits        = (1),
        l_window::Int = -1)
```

Get BitVector of indices for further analysis via DataFrame lookup.

**Arguments:**

  * `xyz`:     `XYZ` flight data struct
  * `line`:    line number
  * `df_line`: lookup table (DataFrame) of `lines`

| **Field**  | **Type** | **Description**                                            |
|:---------- |:-------- |:---------------------------------------------------------- |
| `flight`   | `Symbol` | flight name (e.g., `:Flt1001`)                             |
| `line`     | `Real`   | line number, i.e., segments within `flight`                |
| `t_start`  | `Real`   | start time of `line` to use [s]                            |
| `t_end`    | `Real`   | end   time of `line` to use [s]                            |
| `map_name` | `Symbol` | (optional) name of magnetic anomaly map relevant to `line` |

  * `splits`:   (optional) data splits, must sum to 1
  * `l_window`: (optional) trim data by `N % l_window`, `-1` to ignore

**Returns:**

  * `ind`: BitVector (or tuple of BitVector) of selected data indices
