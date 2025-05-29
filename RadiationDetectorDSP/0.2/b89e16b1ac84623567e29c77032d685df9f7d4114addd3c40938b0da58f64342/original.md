```
struct DifferentiatorFilter <: AbstractRadIIRFilter
```

An integrator filter. It's inverse is [`IntegratorFilter`](@ref).

Constructors:

  * `DifferentiatorFilter(fields...)`

Fields:

  * `gain::Union{Real, Unitful.AbstractQuantity{<:Real}}`: Filter gain
