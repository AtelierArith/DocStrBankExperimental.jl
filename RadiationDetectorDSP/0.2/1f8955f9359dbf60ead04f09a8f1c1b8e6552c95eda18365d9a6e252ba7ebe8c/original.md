```
struct CRFilter <: AbstractRadIIRFilter
```

A first-order CR highpass filter.

The inverse filter is [`InvCRFilter`](@ref), this is typically stable even in the presence of additional noise. This is because a CR filter passes high-frequency noise and so it's inverse passes such noise as well without amplifying it.

Constructors:

  * `CRFilter(fields...)`

Fields:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR time constant
