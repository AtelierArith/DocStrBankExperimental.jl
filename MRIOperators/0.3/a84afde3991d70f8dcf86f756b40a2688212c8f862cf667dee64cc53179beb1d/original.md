```
encodingOp_multiEcho_parallel(acqData::AcquisitionData{T,D}, shape::NTuple{D,Int64}
                                      , senseMaps::Array{Complex{T}}
                                      ; kargs...) where {T,D}
```

generates a LinearOperator which describe combined signal encoding of all the contrasts in an MRI acquisition (for a given slice). The different coils are taken into account in terms of their sensitivities

# Arguments

  * `acqData::AcquisitionData{T,D}`       - AcquisitionData object
  * `shape::NTuple{2,Int64}`              - size of image to be encoded/reconstructed
  * `senseMaps::Array{Complex{T}}`        - coil sensitivities
