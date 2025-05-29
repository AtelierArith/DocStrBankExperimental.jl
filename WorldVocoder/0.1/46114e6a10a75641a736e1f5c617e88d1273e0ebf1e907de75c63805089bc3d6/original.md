```
synthesis(f0::Vector{Float64}, spectrogram::Matrix{Float64}, aperiodicity::Matrix{Float64}, fs::Int, frame_period::Float64 = DEFAULT_FRAME_PERIOD)
```

Synthesize an audio signal `y::Vector{Float64}` using WORLD from and `f0` track, a spectrogram, and an aperiodicity map, at the sampling rate `fs` per second. Optionally specify a `frame_period` in milliseconds.
