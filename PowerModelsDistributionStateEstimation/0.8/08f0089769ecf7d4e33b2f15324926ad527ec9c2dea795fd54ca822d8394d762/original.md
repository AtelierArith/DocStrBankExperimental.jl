```
assign_residual_ub!(data::Dict; chosen_upper_bound::Float64=100, rescale::Bool=false)
```

Basic function that assigns upper bounds to the residual variables, by adding a `"res_max"` entry to the measurement dictionary. The function takes as input either a single measurement dictionary, e.g., `data["meas"]["1"]` or the full measurement dictionary, `data["meas]`.     # Arguments     - data: `ENGINEERING` data model of the feeder, or dictionary corresponding to a single measurement     - chosen*upper*bound: finite upper bound, defaults to 100 if no indication provided     - rescale: `false` by default. If `true`, the `chosen_upper_bound` is multiplied by the value of `data["se_settings"]["rescaler"]`                and their product is used as the upper bound. Otherwise,
