```
mask = CompRoughMask(acq::AcquisitionData, slices::Int64, thresh)
```

Return a rough mask for multiple slices that may not be homogeneous.

# Arguments

  * `acqData::RawAcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `slices::Int64` - number of slices in acquisition data
  * `tresh::Float64` - masking threshold: increase for reduced mask size, decrease for extended mask size

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
