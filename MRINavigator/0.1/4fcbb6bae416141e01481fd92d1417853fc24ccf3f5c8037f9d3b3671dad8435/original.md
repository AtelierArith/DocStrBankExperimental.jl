```
flags = ExtractFlags(rawData::RawAcquisitionData)
```

Extract the acquisition flags from the MRIReco.jl raw data profiles. Return a 31-element vector for each profile.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# Arguments

  * `rawData::RawAcquisitionData` - raw data structure obtained loading raw data with MRIReco.jl
