```
wrap_corr!(nav::Array{Float64, 4}, wrapped_points::Array{Int8, 2}, correlation::Union{Array{Float64, 1}, Matrix{Float64}}, slices::Int64)
```

Unwrap the wrapped points identified with the find_wrapped funtion. These functions can be used only if physiological recording is available.

# Arguments

  * `nav::Array{T, 4}` - phase estimates obtained from the navigator data
  * `wrapped_points::Array{Int8, 2}` - position of the wrapped points, output of find_wrapped
  * `correlation::Union{Array{Float64, 1}` - correlation values between the physiological recording the navigator estimates for each slice. Output of find_wrapped
  * `slices::Int64` - number of slices
