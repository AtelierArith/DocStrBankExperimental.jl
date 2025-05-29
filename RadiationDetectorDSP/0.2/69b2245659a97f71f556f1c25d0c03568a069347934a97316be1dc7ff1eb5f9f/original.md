```
struct InvRCFilter <: AbstractRadIIRFilter
```

Inverse of [`RCFilter`](@ref).

Constructors:

  * `InvRCFilter(fields...)`

Fields:

  * `rc::Union{Real, Unitful.AbstractQuantity{<:Real}}`: RC time constant
