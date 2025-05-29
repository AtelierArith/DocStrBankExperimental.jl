```
sensit = CompSensit(acq::AcquisitionData, thresh = 0.13)
```

Compute the coils sensitivity maps with masking tuned for spinal cord imaging. Use MRICoilSensitivities.jl from MRIReco.jl alternatively.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792

# Arguments

  * `acqData::RawAcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `tresh::Float64` - masking threshold: increase for reduced mask size, decrease for extended mask size
