```
linear_distance(data, synth_data)
```

Compute mean squared (L2) distance between summary statistics.

# Arguments

  * `data::Union{AbstractArray, Real}`: Observed data summary statistics
  * `synth_data::Union{AbstractArray, Real}`: Simulated data summary statistics

# Returns

  * `Float64`: Mean squared difference between data and synth_data

# Notes

  * Handles both scalar and array inputs
  * For arrays, computes element-wise differences before averaging
  * Useful for comparing summary statistics on linear scales
