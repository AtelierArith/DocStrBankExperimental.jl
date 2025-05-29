```
calibrate_instances!(ensemble::WeightedEnsembleNode, climate::Climate, calib_data::Union{AbstractArray,DataFrame}, metric::Union{F,AbstractDict{String,F}}; kwargs...) where {F}
```

Calibrate individual model instances and then the ensemble weights.

# Arguments

  * `ensemble`: WeightedEnsembleNode containing multiple model instances
  * `climate`: Climate data for simulation
  * `calib_data`: Calibration data, either as an array or DataFrame with node names as columns
  * `metric`: Optimization metric function or Dict mapping node names to metrics
  * `kwargs`: Additional arguments passed to BlackBoxOptim

# Returns

  * Tuple of (optimization*result, optimization*setup) from weights calibration
