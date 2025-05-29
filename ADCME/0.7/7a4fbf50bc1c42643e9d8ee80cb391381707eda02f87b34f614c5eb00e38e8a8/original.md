```
dtw(s::Union{PyObject, Array{Float64}}, t::Union{PyObject, Array{Float64}}, 
    use_fast::Bool = false)
```

Computes the dynamic time wrapping (DTW) distance between two time series `s` and `t`.  Returns the distance and path. `use_fast` specifies whether fast algorithm is used. Note  fast algorithm may not be accurate.
