```
Milankovich{T} <: AstroCoord
```

Milankovich Orbital Elements. 7D parameterziation of the orbit. hx - X-component of Angular Momentum Vector hy - Y-component of Angular Momentum Vector hz - Z-component of Angular Momentum Vector ex - X-component of Eccentricity Vector ey - Y-component of Eccentricity Vector ez - Z-component of Eccentricity Vector L - True Longitude

Constructors Milankovich(hx, hy, hz, ex, ey, ez, L) Milankovich(X::AbstractArray) Milankovich(X::AstroCoord, μ::Number)
