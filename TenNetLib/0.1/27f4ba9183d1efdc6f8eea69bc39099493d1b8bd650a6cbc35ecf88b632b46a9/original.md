```
mutable struct DMRGParams
    maxdim::Vector{Int}
    nsweeps::Vector{Int}
    cutoff::Vector{Float64}
    noise::Vector{Float64}
    noisedecay::Vector{Float64}
    disable_noise_after::Vector{Int}
end
```

Holds parameters to control DMRG sweeps.

  * `maxdim::Vector{Int}`: Maximum allowed MPS bond/link dimensions at each stages of DMRG.
  * `nsweeps::Vector{Int}`: Number of sweeps to be performed at each statges of DMRG.
  * `cutoff::Vector{Float64}`: Cutoff for SVD truncation at each stages of DMRG.
  * `noise::Vector{Float64}`: Noise level at each stages of DMRG.
  * `noisedecay::Vector{Float64}`: Decay of noise level at each states of DMRG. Noise is divided by `noisedecay` after each sweep.
  * `disable_noise_after::Vector{Int}`: Switch of noise after this many sweeps at each

states of DMRG.

All these `Vector`s must have same dimension.
