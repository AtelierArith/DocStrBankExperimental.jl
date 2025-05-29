ExaCore([array_eltype::Type; backend = backend, minimize = true])

Returns an intermediate data object `ExaCore`, which later can be used for creating `ExaModel`

## Example

```jldoctest
julia> using ExaModels

julia> c = ExaCore()
An ExaCore

  Float type: ...................... Float64
  Array type: ...................... Vector{Float64}
  Backend: ......................... Nothing

  number of objective patterns: .... 0
  number of constraint patterns: ... 0

julia> c = ExaCore(Float32)
An ExaCore

  Float type: ...................... Float32
  Array type: ...................... Vector{Float32}
  Backend: ......................... Nothing

  number of objective patterns: .... 0
  number of constraint patterns: ... 0

julia> using CUDA

julia> c = ExaCore(Float32; backend = CUDABackend())
An ExaCore

  Float type: ...................... Float32
  Array type: ...................... CUDA.CuArray{Float32, 1, CUDA.DeviceMemory}
  Backend: ......................... CUDA.CUDAKernels.CUDABackend

  number of objective patterns: .... 0
  number of constraint patterns: ... 0
```
