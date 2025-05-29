```
`regrid(acqData::AcquisitionData{T}, kspaceSize::NTuple{2,Int64}
          ; cgnr_iter::Int64=3, correctionMap::Array{Complex{T}}=Complex{T}[]) where (D,T)`
```

Regrid non-cartesian k-space data in `acqData` to a cartesian grid of size `kspaceSize`. Uses the CGNR method to invert the non-cartesian Fourier encoding.

# Arguments:

  * `acqData::AcquisitionData{T}`        - AcquisitionData
  * `ksize::NTuple{2,Int64}`          - size of the cartesian k-space grid
  * `cgnr_iter::Int64=3`              - number of CGNR iterations
  * `correctionMao::Array{Complex{T}}`- relaxation/b0 map
