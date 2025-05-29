```
Delaunay{T} <: AstroCoord
```

Delaunay Orbital Elements. 6D parameterziation of the orbit. L - Canonical Keplerian Energy G - Canonical Total Angular Momentum H - Canonical Normal Angular Momentum (Relative to Equator) M - Mean Anomaly ω - Argument of Periapsis Ω - Right Ascention of the Ascending Node

Constructors Delaunay(L, G, H, M, ω, Ω) Delaunay(X::AbstractVector{<:Number}) Delaunay(X::AstroCoord, μ::Number)
