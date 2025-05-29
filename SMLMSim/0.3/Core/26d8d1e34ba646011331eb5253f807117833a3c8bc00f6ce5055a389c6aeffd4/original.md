```
intensity_trace(f::GenericFluor, nframes::Int, framerate::Real; state1=1)
```

Calculate a fluorescence intensity trace by integrating emission during fluorescent state occupancy.

# Arguments

  * `f::GenericFluor`: Fluorophore model containing transition rates (q) and emission rate (γ)
  * `nframes::Int`: Number of frames to simulate
  * `framerate::Real`: Frame rate in Hz
  * `state1::Int=1`: Initial state (default: 1 for fluorescent state)

# Returns

  * `Vector{Float64}`: Integrated photon counts for each frame

# Details

For each frame:

1. Determines state occupancy using CTMC
2. Integrates emission (rate f.γ) during fluorescent state periods
3. Accumulates photons within frame exposure time (1/framerate)

# Example

```julia
fluor = GenericFluor(; γ=10000.0, q=[-10.0 10.0; 1e-1 -1e-1])
photons = intensity_trace(fluor, 1000, 10.0)
```

# Note

  * State 1 is assumed to be the fluorescent state
  * Emission only occurs in state 1 with rate f.γ
  * Frame exposure is assumed to be 1/framerate (100% duty cycle)
