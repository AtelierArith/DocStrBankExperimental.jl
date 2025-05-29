```
struct InvCRFilter <: AbstractRadIIRFilter
```

Inverse of [`CRFilter`](@ref).

Constructors:

  * `InvCRFilter(fields...)`

Fields:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR time constant
