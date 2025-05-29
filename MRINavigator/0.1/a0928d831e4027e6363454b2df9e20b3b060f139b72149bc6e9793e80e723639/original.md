```
nav = TE_corr!(nav::Array{T, 4}, acqd::AcquisitionData, dt_nav::Float64, TE_nav::Float64, numsamples::Int64, numechoes::Int64) where {T}
```

Compute the phase value for the navigator correction basing on the exact acquisition time of each data sample in the line and for each echo. Return a four-dimensional navigator array.

# Arguments

  * `nav::Array{T, 4}` - phase estimates obtained from the navigator data
  * `acqData::AcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `dt_nav::Float64` - time interval between two samples in the frequency encoding direction
  * `TE_nav::Float64` - echo time of the navigator readout
  * `numsamples::Int64` - number of samples for each profile
  * `numechoes::Int64` - number of echoes

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
