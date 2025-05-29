```
struct IntegratorCRFilter <: AbstractRadIIRFilter
```

A modified CR-filter. The filter has an inverse.

Constructors:

  * `IntegratorCRFilter(fields...)`

Fields:

  * `gain::Union{Real, Unitful.AbstractQuantity{<:Real}}`: Filter gain
  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR time constant
