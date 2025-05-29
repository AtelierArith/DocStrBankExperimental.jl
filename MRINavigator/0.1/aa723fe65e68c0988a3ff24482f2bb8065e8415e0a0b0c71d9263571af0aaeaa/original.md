```
img = Reconstruct(acqd::AcquisitionData, sensit::Array{Complex{T},4}, noisemat::Union{Array{Complex{T}},Nothing} = nothing)
```

Call MRIReco.jl reconstruction function and return reconstructed image. Only single repetition in input.

# Arguments

  * `acqData::RawAcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `sensit::Array{Complex{T},4}` - coil sensitivity map matrix computed with CompSensit(acq::AcquisitionData, thresh = 0.135)
  * `noisemat::Union{Array{Complex{T}},Nothing} = nothing` - noise data extracted from the raw data structure with ExtractNoiseData!(rawData::RawAcquisitionData)

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
