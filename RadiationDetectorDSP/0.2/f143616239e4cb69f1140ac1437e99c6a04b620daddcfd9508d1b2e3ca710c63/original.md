```
abstract type AbstractRadSigFilter{FT<:FilteringType} <: Function
```

Abstract type for signal filters.

Filters are callable as `(flt::AbstractRadSigFilter)(input)` and come with specialized broadcasting.

Subtypes of `AbstractRadSigFilter` must implement

```
fltinstance(flt::AbstractRadSigFilter, si::SamplingInfo)::[`AbstractRadSigFilterInstance`](@ref)
```

Invertible filters should also implement

  * `InverseFunctions.inverse(flt::SomeFilter)`

Note that while a filter may have an inverse, it may, depending on the filter paramters, be very unstable in the presence of additional noise. Filters with a high-pass characteristic pass high-frequency noise, so their inverses pass such noise as well without amplifying it (substantially). Filters with a low-pass characteristic, on the other hand, attentuate high-frequency noise, so their inverses amplify such noise and are typically not useful to deconvolve signals in practical applications.
