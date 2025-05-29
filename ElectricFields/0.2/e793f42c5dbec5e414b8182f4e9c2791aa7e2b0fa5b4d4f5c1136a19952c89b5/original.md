```
field_amplitude_spectrum(f::AbstractField, ω)
```

Compute the analytic Fourier transform of the [`field_amplitude`](@ref) of the field `f` at the angular frequency `ω`, using the Fourier identity

$$
\vec{F}(t) = -\partial_t \vec{A}(t)
\iff
\hat{\vec{F}}(\omega) = -\im\omega \hat{\vec{A}}(\omega)
$$
