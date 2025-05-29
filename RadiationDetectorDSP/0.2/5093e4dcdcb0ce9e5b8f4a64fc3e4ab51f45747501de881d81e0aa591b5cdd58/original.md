```
struct InvModCRFilter <: AbstractRadIIRFilter
```

Inverse of [`ModCRFilter`](@ref).

Constructors:

  * `InvModCRFilter(fields...)`

Fields:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR time constant
