```
phase_vocoder(x, sr = framerate(x); kwargs...)
```

Phase vocoder for time scaling of signal `x` having sampling rate `sr` in Hz. The time-stretch is determined by the ratio of `hopin` and `hopout` variables. For example, `hopin=242` and `hopout=161.3333` (integers are not required) increases the tempo by `hopin/hopout = 1.5`. To slow down a comparable amount, choose `hopin = 161.3333`, `hopout = 242`.

# Option

  * `time::Real = length(x) * sr` : total time to process (in sec)
  * `hopin::Real = 121` : hop length for input
  * `hopout::Real = 2*hopin` : hop length for output
  * `all2pi::Any = 2π*(0:100)` multiples of 2π (used in PV-style freq search)
  * `max_peak::Int = 50` : parameters for peak finding: number of peaks
  * `eps_peak::Real = 0.005` : minimum height of peaks
  * `nfft::Int = 2^12` : fft length
  * `win::AbstractVector{<:Real} = hann(nfft)` : window
  * `T::DataType = Float32` : data type
