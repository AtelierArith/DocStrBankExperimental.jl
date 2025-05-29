```
struct SimpleCSAFilter <: AbstractRadIIRFilter
```

Simulates the current-signal response of a charge-sensitive preamplifier with resistive reset, the output is a charge signal.

It is equivalent to the composition

```julia
CRFilter(cr = tau_decay) ∘
Integrator(gain = gain) ∘
RCFilter(rc = tau_rise)
```

and maps to a single `BiquadFilter`.

This filter has an inverse, but the inverse is very unstable in the presence of additional noise if `tau_rise` is not zero (since the inverse of an RC-filter is unstable under noise). Even if `tau_rise` is zero the inverse will still amplify noise (since it differentiates), so it should be used very carefully when deconvolving signals in practical applications.

Constructors:

  * `SimpleCSAFilter(fields...)`

Fields:

  * `tau_rise::Union{Real, Unitful.AbstractQuantity{<:Real}}`: Rise time constant
  * `tau_decay::Union{Real, Unitful.AbstractQuantity{<:Real}}`: Decay time constant
  * `gain::Union{Real, Unitful.AbstractQuantity{<:Real}}`: Gain
