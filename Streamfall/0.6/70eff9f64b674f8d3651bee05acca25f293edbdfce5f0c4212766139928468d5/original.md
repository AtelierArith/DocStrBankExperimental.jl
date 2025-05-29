```
calibrate!(
    node::NetworkNode,
    climate::Climate,
    calib_data::AbstractArray,
    metric::Union{C,AbstractDict{String,C}};
    kwargs...
) where {C}
```

Calibrate a given node using the BlackBoxOptim package.

# Arguments

  * `node::NetworkNode` : Streamfall node
  * `climate` : Climate data
  * `calib_data` : calibration data for target node by its id
  * `extractor::Function` : Calibration extraction method, define a custom one to change behavior
  * `metric::Function` : Optimization function to use. Defaults to RMSE.
