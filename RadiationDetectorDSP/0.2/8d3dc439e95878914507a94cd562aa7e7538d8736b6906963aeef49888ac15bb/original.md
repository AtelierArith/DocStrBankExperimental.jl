```
struct ModCRFilter <: AbstractRadIIRFilter
```

A first-order CR highpass filter, modified for full-amplitude step-signal response.

The resonse of the standard digital [`CRFilter`](@ref) will not recover the full amplitude of a digital step stignal since a step from one sample to the still has a finite rise time. This version of a CR filter compensates for this loss in amplitude, so it effectively treats a step as having

The inverse filter is [`InvModCRFilter`](@ref), this is typically stable even in the presence of additional noise (see [`CRFilter`](@ref)).

Constructors:

  * `ModCRFilter(fields...)`

Fields:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR time constant
