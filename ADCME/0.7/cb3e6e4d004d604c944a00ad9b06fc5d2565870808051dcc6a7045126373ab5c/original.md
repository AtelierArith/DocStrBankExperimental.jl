```
convert_to_tensor(o::Union{PyObject, Number, Array{T}, Missing, Nothing}; dtype::Union{Type, Missing}=missing) where T<:Number
convert_to_tensor(os::Array, dtypes::Array)
```

Converts the input `o` to tensor. If `o` is already a tensor and `dtype` (if provided) is the same as that of `o`, the operator does nothing. Otherwise, `convert_to_tensor` converts the numerical array to a constant tensor or casts the data type. `convert_to_tensor` also accepts multiple tensors. 

# Example

```julia
convert_to_tensor([1.0, constant(rand(2)), rand(10)], [Float32, Float64, Float32])
```
