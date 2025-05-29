```
GlaOpr(cel::NTuple{3, Int}, scl::NTuple{3, Rational}, 
org::NTuple{3, Rational}=(0//1, 0//1, 0//1); 
useGpu::Bool=false, setTyp::DataType=ComplexF64)
```

Construct a self Green operator.

# Arguments

  * `cel::NTuple{3, Int}`: The number of cells in each dimension.
  * `scl::NTuple{3, Rational}`: The size of each cell in each dimension

(in units of wavelength).

  * `org::NTuple{3, Rational}=(0//1, 0//1, 0//1)`: The origin of the volume in

each dimension (in units of wavelength).

  * `useGpu::Bool=false`: Whether to use the GPU (true) or CPU (false).
  * `setTyp::DataType=ComplexF64`: The element type of the operator. Must be a

subtype of `Complex`.
