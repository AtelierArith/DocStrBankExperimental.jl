```
promote_itensor_eltype(m::MPS)
promote_itensor_eltype(m::MPO)
```

Return the promotion of the elements type of the tensors in the MPS or MPO. For example, if all tensors have type `Float64` then return `Float64`. But if one or more tensors have type `ComplexF64`, return `ComplexF64`.
