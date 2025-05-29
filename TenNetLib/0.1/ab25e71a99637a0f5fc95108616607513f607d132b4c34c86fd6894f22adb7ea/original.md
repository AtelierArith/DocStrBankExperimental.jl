```
mutable struct OptimizeParamsTTN
    maxdim::Vector{Int}
    nsweeps::Vector{Int}
    cutoff::Vector{Float64}
    noise::Vector{Float64}
    noisedecay::Vector{Float64}
    disable_noise_after::Vector{Int}
end
```

Holds parameters to control the optimzation sweeps of the TTN.

  * `maxdim::Vector{Int}`: Maximum allowed TTN bond/link dimensions at each stages of optimization.
  * `nsweeps::Vector{Int}`: Number of sweeps to be performed at each statges of optimization.
  * `cutoff::Vector{Float64}`: Cutoff for SVD truncation at each stages of optimization.
  * `noise::Vector{Float64}`: Noise level at each stages of optimization.
  * `noisedecay::Vector{Float64}`: Decay of noise level at each states of optimization.

Noise is divided by `noisedecay` after each sweep.

  * `disable_noise_after::Vector{Int}`: Switch of noise after this many sweeps at each

states of optimization.

All these `Vector`s must have same dimension.
