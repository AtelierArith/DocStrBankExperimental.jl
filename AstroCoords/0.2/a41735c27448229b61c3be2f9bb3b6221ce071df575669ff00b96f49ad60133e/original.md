```
Keplerian{T} <: AstroCoord
```

Keplerian Orbital Elements. 6D parameterziation of the orbit. a - semi-major axis e - eccetricity  i - inclination  Ω - Right Ascension of Ascending Node  ω - Argument of Perigee f - True Anomaly

Constructors Keplerian(a, e, i, Ω, ω, f) Keplerian(X::AbstractArray) Keplerian(X::AstroCoord, μ::Number)
