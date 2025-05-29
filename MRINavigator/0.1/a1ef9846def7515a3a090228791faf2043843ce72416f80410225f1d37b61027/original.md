```
img = directreco(acq::AcquisitionData)
```

Call MRIReco.jl reconstruction function and return reconstructed image. Reconstruct coils separately.

# Arguments

  * `acqData::RawAcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
