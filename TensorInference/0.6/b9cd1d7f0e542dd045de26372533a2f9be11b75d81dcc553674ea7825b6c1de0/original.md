```julia
struct RescaledArray{T, N, AT<:AbstractArray{T, N}} <: AbstractArray{T, N}
```

```
RescaledArray(α, T) -> RescaledArray
```

An array data type with a log-prefactor, and a l∞-normalized storage, i.e. the maximum element in a tensor is 1. This tensor type can avoid the potential underflow/overflow of numbers in a tensor network. The constructor `RescaledArray(α, T)` creates a rescaled array that equal to `exp(α) * T`.
