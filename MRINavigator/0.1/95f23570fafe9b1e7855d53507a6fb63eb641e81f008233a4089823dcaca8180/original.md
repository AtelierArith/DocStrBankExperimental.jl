```
CopyTE!(rawData::RawAcquisitionData, acqData::AcquisitionData)
```

Copy the TE values from the MRIReco.jl raw data structure to the acquisition data structure.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# Arguments

  * `rawData::RawAcquisitionData` - raw data structure obtained loading raw data with MRIReco.jl
  * `acqData::AcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
