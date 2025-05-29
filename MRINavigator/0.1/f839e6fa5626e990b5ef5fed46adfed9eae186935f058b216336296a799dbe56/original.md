```
sensit = ResizeSensit!(sensit::Array{Complex{T},4}, acqMap::AcquisitionData, acqData::AcquisitionData)
```

Resize and resample the coil sensitivity map to match the acquisition data field of view and resolution. This step is needed for the image reconstruction to run. Image data and reference data must have the same slice center.

# Arguments

  * `sensit::Array{Complex{T},4}` - output of CompSensit(acq::AcquisitionData, thresh)
  * `acqMap::RawAcquisitionData` - acquisition data structure obtained converting raw reference data with MRIReco.jl
  * `acqData::RawAcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
