```
convertRawToAcq(rawData::::RawAcquisitionData)
```

Convert raw data to acquisition data using MRIReco.jl, then apply small adjustments. Return acquisition data structure.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# Arguments

  * `rawData::RawAcquisitionData` - raw data structure obtained loading raw data with MRIReco.jl
