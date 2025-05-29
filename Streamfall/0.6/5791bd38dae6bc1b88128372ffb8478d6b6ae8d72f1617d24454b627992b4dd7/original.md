```
calibrate!(
    node::NetworkNode, climate::Climate, calib_data::DataFrame,
    metric::Union{C,AbstractDict{String,C}};
    kwargs...
) where {C}
```

Calibrate a given node using the BlackBoxOptim package.

# Arguments

  * `node::NetworkNode` : Streamfall node
  * `climate` : Climate data
  * `calib_data` : Calibration data for target node, where column names indicate node names
  * `metric::Function` : Optimization function to use.
