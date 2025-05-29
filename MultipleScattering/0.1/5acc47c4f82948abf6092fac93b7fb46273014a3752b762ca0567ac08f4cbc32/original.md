```
internal_field(x::AbstractVector, p::Particle{Dim,Acoustic{T,Dim}},  source::RegularSource, ω::T, scattering_coefficients::AbstractVector{Complex{T}})
```

The internal field for an acoustic particle in an acoustic medium. For a sphere and circular cylinder the result is exact, for everything else it is an approximation which assumes smooth fields.
