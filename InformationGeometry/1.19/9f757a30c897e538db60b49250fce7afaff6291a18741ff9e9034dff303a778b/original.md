```
Deplanarize(PL::Plane,sol::AbstractODESolution; N::Int=500) -> Matrix
Deplanarize(PL::Plane,sol::AbstractODESolution, Ts::AbstractVector{<:Number}) -> Matrix
```

Converts the 2D outputs of `sol` from planar coordinates associated with `PL` to the coordinates of the ambient space of `PL`.
