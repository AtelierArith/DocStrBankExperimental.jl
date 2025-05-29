```
POVMel( M :: AbstractMatrix{T<:Number}; atol=ATOL :: Float64) <: Operator{T}
```

A [`POVM`](@ref) element. A `DomainError` is thrown if matrix `M` is not hermitian and positive semi-definite within absolute tolerance `atol`.
