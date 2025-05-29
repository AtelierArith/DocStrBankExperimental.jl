```
encodingOps_parallel(acqData::AcquisitionData{T,D}, shape::NTuple{D,Int64}
                          , senseMaps::Array{Complex{T}}
                          ; kargs...) where {T,D}
```

generates an Array of LinearOperators which describe signal encoding of the individual contrasts in an MRI acquisition. The different coils are taken into account in terms of their sensitivities

# Arguments

  * `acqData::AcquisitionData{T,D}`       - AcquisitionData object
  * `shape::NTuple{D,Int64}`              - size of image to be encoded/reconstructed
  * `senseMaps::Array{Complex{T}}`        - coil sensitivities
