```
noisemat = ExtractNoiseData!(rawData::RawAcquisitionData, flags::Array{Int64})
```

Extract and return the noise acquisition from the MRIReco.jl raw data. The noise acquisition is usually the first profile with slice = 0, contrast = 0, repetition = 0. The noise profile should have the 19th flag element equal to 1. Check this with ExtractFlags if errors occur.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# Arguments

  * `rawData::RawAcquisitionData` - raw data structure obtained loading raw data with MRIReco.jl
