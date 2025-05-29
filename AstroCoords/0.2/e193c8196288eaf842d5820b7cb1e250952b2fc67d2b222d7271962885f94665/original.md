```
ModEq{T} <: AstroCoord
```

Modified Equinoctial Orbital Elements. 6D parameterziation of the orbit. p - semi-parameter f - eccetricity projection onto longitude of perigee g - eccetricity projection onto ⟂ longitude of perigee h - projection of half inclination onto RAAN k - projection of half inclination onto ⟂ RAAN L - true longitude

Constructors ModEq(p, f, g, h, k, l) ModEq(X::AbstractArray) ModEq(X::AstroCoord, μ::Number)
