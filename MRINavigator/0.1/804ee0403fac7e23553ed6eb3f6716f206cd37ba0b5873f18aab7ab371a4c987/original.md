```
apply_corr!(nav::Array{T, 4}, acqd::AcquisitionData, numechoes::Int64, numlines::Int64, numsamples::Int64, numslices::Int64) where {T}
```

Apply the navigator-based correction to the acquisition data structure obtained loading the raw data with MRIReco.jl. After applying the correction the image should be reconstructed. Use the reconstruct function.

# Arguments

  * `nav::Array{T, 4}` - phase estimates obtained from the navigator data
  * `acqd::AcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `numechoes::Int64` - number of echoes
  * `numlines::Int64` - number of lines (profiles) for each slice and echo
  * `numsamples::Int64` - number of samples for each profile
  * `numslices::Int64` - number of slices

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
