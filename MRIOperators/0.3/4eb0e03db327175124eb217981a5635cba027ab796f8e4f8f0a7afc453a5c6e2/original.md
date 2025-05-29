```
encodingOp_multiEcho(acqData::AcquisitionData{T,D}, shape::NTuple{D,Int64}; kargs...) where {T,D}
```

generates a LinearOperator which describe combined signal encoding of all the contrasts in an MRI acquisition (for a given slice).

# Arguments

  * `acqData::AcquisitionData`            - AcquisitionData object
  * `shape::NTuple{D,Int64}`              - size of image to be encoded/reconstructed
