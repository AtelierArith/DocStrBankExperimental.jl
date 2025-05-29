```
struct RCFilter <: AbstractRadII>RFilter
```

A first-order RC lowpass filter.

The inverse filter is [`InvCRFilter`](@ref), but note that this is unstable in the presence of additional noise. As an RC filter attenuates high-frequency noise, its inverse amplifies such noise and will typically not be useful to deconvolve signals in practical applications.

Constructors:

  * `RCFilter(fields...)`

Fields:

  * `rc::Union{Real, Unitful.AbstractQuantity{<:Real}}`: RC time constant
