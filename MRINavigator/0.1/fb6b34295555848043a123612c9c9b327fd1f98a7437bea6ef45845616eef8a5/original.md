```
find_wrapped(nav::Array{Float64, 4}, nav_time::Array{Float64, 2}, trace::Array{Float64, 2}, slices::Int64)
```

Identify the position of the wrapped points in the navigator phase estimates. The respiratory belt recording is necessary. Return the position of the wrapped points, the correlation between each navigator slice and the trace data, the aligned and interpolated trace data.

# Arguments

  * `nav::Array{Float64, 4}`      - navigator phase estimates
  * `nav_time::Array{Float64, 2}` - navigator data timestamps in ms from the beginning of the day, for each slice
  * `trace::Array{Float64, 2}`    - physiological trace recording. Two columns vector (1:time [ms], 2:trace). The first column contains the timestamps in ms from the beginning of the day.                                   Include time points before and after the image acquisition (at least 2 s).
  * `slices::Int64`               - number of slices
