```
OrderSlices!(rawData::RawAcquisitionData)
```

Spatially order the slices in the MRIReco.jl raw data structure. The slices are ordered basing on the position coordinates saved in each profile. If these are not present the slices can not be ordered.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# Arguments

  * `rawData::RawAcquisitionData` - raw data structure obtained loading raw data with MRIReco.jl
