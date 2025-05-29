```
FermiSurface(reciprocalspace::Union{BrillouinZone, ReciprocalZone}, μ::Real=0.0, bands::Union{Colon, AbstractVector{Int}}=:, orbitals::AbstractVector{Int}...)
FermiSurface(reciprocalspace::Union{BrillouinZone, ReciprocalZone}, μ::Real, bands::Union{Colon, AbstractVector{Int}}, orbitals::Tuple{Vararg{AbstractVector{Int}}})
```

`FermiSurface`を構築します。
