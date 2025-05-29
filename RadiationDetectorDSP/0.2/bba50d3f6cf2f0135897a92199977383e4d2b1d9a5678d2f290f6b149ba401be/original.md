```
struct SamplingInfo{T<:RealQuantity,A<:AbstractVector{<:RealQuantity}}
```

Holds sampling information.

The numerical type of an individual sample is `T`, the (time) axis is given by the `axis` field.

Constructors:

  * `SamplingInfo{T,A}(axis)`
  * `SamplingInfo{T}(axis)`

Fields:

  * `axis::AbstractVector{<:Union{Real, Unitful.AbstractQuantity{<:Real}}}`
