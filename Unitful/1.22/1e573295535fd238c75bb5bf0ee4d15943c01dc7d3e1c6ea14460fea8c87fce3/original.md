```
struct Gain{L, S, T<:Real} <: LogScaled{L}
```

A logarithmic scale-based gain or attenuation factor. This type has one field, `val::T`. For example, given a gain of `20dB`, we have `val===20`. This type differs from [`Unitful.Level`](@ref) in that `val` is stored after computing the logarithm.
