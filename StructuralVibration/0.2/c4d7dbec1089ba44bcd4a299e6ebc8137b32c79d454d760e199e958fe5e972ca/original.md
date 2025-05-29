```
FFTParameters
```

Structure to store the time and frequency parameters for the FFT analysis

**Constructor**

  * `fs::Real`: Sampling rate of the signal
  * `bs::Real`: Block size of the signal
  * `pow2::Bool`: Flag for finding the next power of 2

**Fields**

  * `t::AbstractRange`: Time vector
  * `dt::Float64`: Time step
  * `tspan::Tuple{Float64, Float64}`: Time span
  * `freq::AbstractRange`: Frequency vector
  * `df::Float64`: Frequency resolution
  * `freq_span::Tuple{Float64, Float64}`: Frequency span
  * `fs::Int`: Sampling rate
  * `bs::Int`: Block size
