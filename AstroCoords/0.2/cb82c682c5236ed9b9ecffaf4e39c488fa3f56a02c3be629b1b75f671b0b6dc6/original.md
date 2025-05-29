```
J2EqOE{T} <: AstroCoord
```

Modified Equinoctial Orbital Elements. 6D parameterziation of the orbit. n - mean motion h - eccetricity projection onto longitude of perigee k - eccetricity projection onto ⟂ longitude of perigee p - projection of half inclination onto RAAN q - projection of half inclination onto ⟂ RAAN L - true longitude

Constructors J2EqOE(n, h, k, p, q, L) J2EqOE(X::AbstractArray) J2EqOE(X::AstroCoord, μ::Number)
