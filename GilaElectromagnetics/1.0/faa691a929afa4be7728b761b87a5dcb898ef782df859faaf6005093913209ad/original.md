```
GlaOpr(celSrc::NTuple{3, Int}, sclSrc::NTuple{3, Rational}, 
orgSrc::NTuple{3, Rational}, celTrg::NTuple{3, Int}, 
sclTrg::NTuple{3, Rational}, orgTrg::NTuple{3, Rational}; 
useGpu::Bool=false, setTyp::DataType=ComplexF64)
```

Construct an external Green's operator.

# Arguments

  * `celSrc::NTuple{3, Int}`: The number of cells in each dimension of the source

volume.

  * `sclSrc::NTuple{3, Rational}`: The size of each cell in each dimension of the

source volume (in units of wavelength).

  * `orgSrc::NTuple{3, Rational}`: The origin of the source volume in each

dimension (in units of wavelength).

  * `celTrg::NTuple{3, Int}`: The number of cells in each dimension of the target

volume.

  * `sclTrg::NTuple{3, Rational}`: The size of each cell in each dimension of the

target volume (in units of wavelength).

  * `orgTrg::NTuple{3, Rational}`: The origin of the target volume in each

dimension (in units of wavelength).

  * `useGpu::Bool=false`: Whether to use the GPU (true) or CPU (false).
  * `setTyp::DataType=ComplexF64`: The element type of the operator. Must be a

subtype of `Complex`.
