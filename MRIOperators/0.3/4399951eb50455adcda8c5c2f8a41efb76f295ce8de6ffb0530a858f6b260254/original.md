```
encodingOps_simple(acqData::AcquisitionData, shape::NTuple{D,Int64}
                          ; kargs...) where D
```

generates an Array of LinearOperators which describe signal encoding of the individual contrasts in an MRI acquisition (for a given slice).

# Arguments

  * `acqData::AcquisitionData`            - AcquisitionData object
  * `shape::NTuple{D,Int64}`              - size of image to be encoded/reconstructed
