See also: [`ContinuousImpulse`](@ref), [`TimeDiracImpulse`](@ref)

```
GaussianImpulse(maxω[; σ = 3.0/maxω^2])
```

Returns a gaussian impulse function, which in the frequency domain is `exp(-σ*ω^2)*(2sqrt(σ*pi))`.
