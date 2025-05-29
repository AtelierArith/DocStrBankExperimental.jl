```
FieldmapNFFTOp(shape::NTuple{D,Int64}, tr::Trajectory,
                    correctionmap::Array{ComplexF64,D};
                    method::String="nfft",
                    echoImage::Bool=true,
                    alpha::Float64=1.75,
                    m::Float64=3.0,
                    K=20,
                    kargs...) where D
```

generates a `FieldmapNFFTOp` which evaluates the MRI Fourier signal encoding operator, including B0-inhomogeneities using time-segmented NFFTs.

# Arguments:

  * `shape::NTuple{D,Int64}`             - size of image to encode/reconstruct
  * `tr::Trajectory`                     - Trajectory with the kspace nodes to sample
  * `correctionmap::Array{ComplexF64,D}` - fieldmap for the correction of off-resonance effects
  * (`method::String="nfft"`)            - method to use for time-segmentation when correctio field inhomogeneities
  * (`echoImage::Bool=false`)            - if true sampling times will only be considered relative to the echo time                                        this results in complex valued image even for real-valued input.
  * (`alpha::Float64=1.75`)              - oversampling factor for interpolation
  * (`m::Float64=3.0`)                   - truncation size of interpolation kernel
  * (`K=20`)                             - number of translates for LeastSquares approaches                                        (not NFFT-approach) to time-segmentation
  * (`kargs`)                            - additional keyword arguments
