```
QuantizedArray{Q<:AbstractQuantization,U<:Unsigned,D<:PreMetric,T,N} <: AbstractArray{T,N}
```

A quantized array. It represents a 'quantized' representation of an original array, equivalent to a lossy compressed version.

# Fields

  * `quantizer::ArrayQuantizer{Q,U,D,T,N}` the quantized of the array
  * `data::Matrix{U}` the actual compressed representation of the quantized array
