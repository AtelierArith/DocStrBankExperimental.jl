```
struct IntegratorFilter <: AbstractRadIIRFilter
```

An integrator filter. It's inverse is [`DifferentiatorFilter`](@ref).

Constructors:

  * `IntegratorFilter(fields...)`

Fields:

  * `gain::Union{Real, Unitful.AbstractQuantity{<:Real}}`: Filter gain
