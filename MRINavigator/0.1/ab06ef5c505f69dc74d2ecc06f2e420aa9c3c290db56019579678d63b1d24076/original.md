```
CompResizeSaveSensit(acqMap::AcquisitionData, acqData::AcquisitionData, path_sensit::String)
```

Compute, resize to the image data dimension and save the coils sensitivity maps with masking tuned for spinal cord imaging. Use MRICoilSensitivities.jl from MRIReco.jl alternatively.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# Arguments

  * `acqMap::RawAcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `acqData::RawAcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `tresh::Float64` - masking treshold: increase for reduced mask size, decrease for extended mask size
