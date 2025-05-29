```
Data = additionalNavInput(
    noisemat::Array{Complex{Float32}, 2},
    rawData::RawAcquisitionData,
    acqData::AcquisitionData,
    acqMap::Union{AcquisitionData, Nothing} = nothing,
    nav_time::Union{Array{Complex{Float32}, 2}, Nothing} = nothing,
    trace::Union{Matrix{Float64}, Nothing} = nothing,
    centerline::Union{Vector{Float64}, Nothing} = nothing)
```

Construct the additional data structure that is needed as input to navCorr!

# Arguments

  * `noisemat::Array{Complex{Float32}, 2}` - noise data obtained with ExtractNoiseData!
  * `rawData::RawAcquisitionData` - raw data structure obtained loading raw data with MRIReco.jl
  * `acqData::AcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl

# Optional arguments with default value = nothing

  * `acqMap::Union{AcquisitionData, Nothing} = nothing`       - acquisition data structure obtained converting reference data with MRIReco.jl
  * `nav_time::Union{Array{Complex{Float32}, 2}, Nothing}`    - time stamps for the navigator data obtained with ExtractNavigator (in ms from the beginning of the day)
  * `trace::Union{Matrix{Float64}, Nothing}`                  - respiratory trace time stamps and values in matrix with two colunms (1:time [ms], 2:trace).                                                               Include time points before and after the image acquisition (at least 2 s).
  * `centerline::Union{Vector{Float64}, Nothing}`             - coordinates of the spinal cord ceterline obtained with callSCT

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
