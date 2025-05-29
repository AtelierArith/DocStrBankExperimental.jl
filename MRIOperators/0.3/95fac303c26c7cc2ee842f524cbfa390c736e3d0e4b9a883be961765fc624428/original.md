```
ExplicitOp(shape::NTuple{D,Int64}, tr::Trajectory, correctionmap::Array{ComplexF64,D}
        ; echoImage::Bool=false, kargs...) where D
```

generates a `ExplicitOp` which explicitely evaluates the MRI Fourier signal encoding operator.

# Arguments:

  * `shape::NTuple{D,Int64}`             - size of image to encode/reconstruct
  * `tr::Trajectory`                     - Trajectory with the kspace nodes to sample
  * `correctionmap::Array{ComplexF64,D}` - fieldmap for the correction of off-resonance effects
  * `echoImage::Bool=false`              - if true sampling times will only be considered relative to the echo time                                        this results in complex valued image even for real-valued input.
  * `kargs`                              - additional keyword arguments
