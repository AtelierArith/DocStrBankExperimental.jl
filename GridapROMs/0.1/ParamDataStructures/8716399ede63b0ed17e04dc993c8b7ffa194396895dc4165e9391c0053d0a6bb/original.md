```
struct ConsecutiveParamArray{T,N,M,A<:AbstractArray{T,M}} <: ParamArray{T,N}
  data::A
end
```

Parametric array with entries stored consecutively in memory. It is characterized by an inner size equal to `size(data)[1:N]`, and parametric length equal to `size(data,N+1)`, where `data` is an `AbstractArray` of dimension `M = N+1`
