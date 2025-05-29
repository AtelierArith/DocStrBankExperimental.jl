```
periodogram(y, t, normalisation = "default"; apply_end_matching = false, subtract_mean = true)
```

Compute the periodogram of the data y with time stamps t using the fast Fourier transform (FFT).

The periodogram is computed as the squared magnitude of the Fourier transform of the data. In practrice we  use the real-valued fast Fourier transform (rfft) to compute the periodogram.

# Arguments

  * `y::Array{Float64, 1}`: Time series data.
  * `t::Array{Float64, 1}`: Time stamps.
  * `normalisation::Float64`: Normalisation factor. Default is 2Δt / length(t).
  * `apply_end_matching::Bool`: Apply end-matching to the data. Default is false.
  * `subtract_mean::Bool`: Subtract the mean from the data. Default is true.
