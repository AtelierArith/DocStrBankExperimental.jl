```
navOutput = NavCorr!(nav::Array{Complex{T}, 4}, acqData::AcquisitionData, params::Dict{Symbol, Any}, addData::additionalNavInput) where {T}
```

Compute the navigator-based correction and apply it to the acquisition data. Multiple pipelines are available: "knav", "FFT" and "FFT*unwrap". Return navigator trace, spinal cord centerline in the reconstructed image coordinates,  Correlation between navigator and belt data for each slice and position of wrapped points for each slices. Please choose the pipeline using the corr*type filed in the params dictionary.

# Arguments

  * `nav::Array{Complex{T}, 4}` - navigator profiles obtained with the ExtractNavigator function
  * `acqData::AcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `params::Dict{Symbol, Any}` - navigator correction paramerters dictionary
  * `addData::additionalNavInput` - mandatory additional data structure obtained with the constructor: additionalNavInput

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
