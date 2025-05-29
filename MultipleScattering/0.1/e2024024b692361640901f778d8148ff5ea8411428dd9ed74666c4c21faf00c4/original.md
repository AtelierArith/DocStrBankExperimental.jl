See also: [`DiscreteImpulse`](@ref), [`frequency_to_time`](@ref)

```
ContinuousImpulse{T<:AbstractFloat}
```

A struct used to represent an analytic impulse function. Has two fields: `in_time` a function of time `t`, and `in_freq` a function of the angular frequency `ω`. `in_freq` should be the Fourier transform of `in_time`, though this is not enforced.

We use the Fourier transform convention: F(ω) =  ∫ f(t)*exp(im*ω*t) dt, f(t) = (2π)^(-1) * ∫ F(ω)*exp(-im*ω*t) dω.

An impluse f(t) is convoluted in time with the field u(t), however we avoid the convolution by working with the fourier transform F(ω) of the impulse f(t), which results in

frequency to time: (2π)^(-1) * ∫ F(ω)*U(ω)*exp(-im*ω*t) dω
