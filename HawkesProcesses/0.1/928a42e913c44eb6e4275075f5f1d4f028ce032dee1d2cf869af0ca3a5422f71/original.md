```
intensity(ts, events, background, kappa, kernel)
```

Evaluate the intensity over a timegrid for some observed events with given Hawkes parameters.

# Arguments

  * `ts::Array{<:Number,1}`: time grid to evalue the intensity over
  * `events::Array{<:Number,1}`: Events of the process
  * `background`: Background rate
  * `kappa::Float64`: Kappa value
  * `kernel::Function`: Kernel function

# Notes

  * `kappa` must be between 0 and 1
