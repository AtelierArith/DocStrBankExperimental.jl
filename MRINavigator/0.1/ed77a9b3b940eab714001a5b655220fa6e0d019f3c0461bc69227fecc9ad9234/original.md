```
RemoveRef!(rawData::RawAcquisitionData, slices::Union{Vector{Int64}, Nothing}, echoes::Union{Vector{Int64}, Nothing})
```

Remove reference data from acquisitions with phase stabilization on Siemens scanners. To be applied before the navigator-based correction. Necessary when the reference data is acquired before the image data. Make sure that this is needed on your data checking the time stamps. For Siemens: It is possible to read raw data with mapVBVD in Matlab. The reference data to be removed is called phasestabRef in mapVBVD. Not robust for sequences with concatenations > 1. Not robust to repeated calls, modifies rawData.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792 mapVBVD reference: https://github.com/CIC-methods/FID-A/blob/master/inputOutput/mapVBVD/README.md

# Arguments

  * `rawData::RawAcquisitionData` - raw data structure obtained loading raw data with MRIReco.jl
