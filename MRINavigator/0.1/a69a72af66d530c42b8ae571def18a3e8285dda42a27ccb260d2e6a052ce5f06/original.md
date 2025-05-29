```
(nav, nav_time) = ExtractNavigator(rawData::RawAcquisitionData, slices::Union{Vector{Int64}, Nothing})
```

Extract the navigator profiles from the MRIReco.jl raw data structure. These are registered with the same indices (contract, slice, encoding step) as the image data for the first echo time. Return a navigator array and a navigator time array. The navigator array has four dimensions in the following order: k-space samples, coils, k-space lines, slices. Effective only if the navigator profile was acquired after the first image profile.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# Arguments

  * `rawData::RawAcquisitionData` - raw data structure obtained loading raw data with MRIReco.jl
