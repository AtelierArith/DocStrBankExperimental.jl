```
AdjustSubsampleIndices!(acqData::AcquisitionData)
```

Add subsamples indices in the MRIReco.jl acquisition data structure. Needed when converting data not acquired in the first repetition.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# Arguments

  * `acqData::AcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
