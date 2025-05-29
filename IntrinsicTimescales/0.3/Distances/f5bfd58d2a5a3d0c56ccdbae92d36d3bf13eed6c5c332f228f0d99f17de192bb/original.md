```
logarithmic_distance(data, synth_data)
```

Compute mean squared distance between logarithms of summary statistics.

# Arguments

  * `data::Union{AbstractArray, Real}`: Observed data summary statistics
  * `synth_data::Union{AbstractArray, Real}`: Simulated data summary statistics

# Returns

  * `Float64`: Mean squared difference between log(data) and log(synth_data)

# Notes

  * Handles both scalar and array inputs
  * For arrays, computes element-wise log differences before averaging
  * Useful for comparing summary statistics spanning multiple orders of magnitude
  * Assumes all values are positive
