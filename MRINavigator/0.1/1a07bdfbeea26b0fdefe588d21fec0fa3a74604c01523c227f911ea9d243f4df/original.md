```
SelectSlice!(acqd, nav, nav_time, idx_slice)
```

Extract one or more echoes from the acquisition data structure

# Arguments

  * `acqd::AcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `idx_slice::Vector{Int64}` - vector containing the indexes of the slices to be selected (starting from 0, downer slice)

# Optional arguments with default value = nothing

  * `nav::Union{Array{Complex{T}, 4}, Nothin} = nothing` - navigator profiles obtained with the ExtractNavigator function
  * `nav_time::Union{Array{Complex{Float32}, 2}, Nothing}` - time stamps for the navigator data obtained with ExtractNavigator (in ms from the beginning of the day)

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
