```
ArrayQuantizer{Q,U,D,T,N}
```

The array quantizer object. It transforms an array with elements of type `T` into a 'quantized' version with elemetns of type `U`.

# Fields

  * `quantization::Q` type of quantization employed i.e. additive, orthogonal
  * `dims::NTuple{N,Int}` the original array dimensionality
  * `codebooks::Vector{CodeBook{U,T}}` the codebooks
  * `k::Int` the number of vector prototypes in each codebooks
  * `distance::D` the distance employed
  * `rot::Matrix{T}` rotation matrix
