```
function DMRGParams(;maxdim::Vector{Int}, nsweeps::Vector{Int}, 
                    cutoff::Union{Vector{Float64}, Float64, Int} = _Float64_Threshold,
                    noise::Union{Vector{Float64}, Float64, Int} = 0.0,
                    noisedecay::Union{Vector{Float64}, Float64, Int} = 1.0,
                    disable_noise_after::Union{Vector{Int}, Int} = typemax(Int))
```

Constructor for `DMRGParams`. Takes only named arguments.

  * `maxdim::Vector{Int}`: Maximum allowed MPS bond/link dimensions at each stages of DMRG.
  * `nsweeps::Vector{Int}`: Number of sweeps to be performed at each statges of DMRG.
  * `cutoff::Union{Int, Float64, Vector{Float64}} = Float64_threshold()`: Cutoff for SVD truncation at each stages of DMRG. If `Float64`, `cutoff` remains same throughout the DMRG simulation.
  * `noise::Union{Float64, Int, Vector{Float64}} = 0.0`: Noise level at each stages of DMRG. If `Float64` or `Int`, initial `noise` remains same throughout the DMRG simulation.
  * `noisedecay::Union{Float64, Int, Vector{Float64}} = 1.0`: Decay of noise level at each states of DMRG. Noise is divided by `noisedecay` after each sweep. If `Float64` or `Int`, `noisedecay` remains same throughout the DMRG simulation.
  * `disable_noise_after::Union{Int, Vector{Int}} = typemax(Int)`: Switch of noise after this many sweeps at each states of DMRG. If `Int`, `disable_noise_after` remains same throughout the DMRG simulation.
