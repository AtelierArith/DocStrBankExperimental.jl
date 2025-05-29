```
INSCH!(Z::Vector{Complex{T}}, E::T, grid::CamiDiff.Grid{T}, def::Def{T}) where T<:Real
```

Ansatz solution for the *inward* integration of the radial wave equation for the first $k$ points  on the [`CamiDiff.Grid`](@extref), where $k$ is the Adams-Moulton order. The Ansatz is based on the WKB solution  for energy `E` at distances *far above* the upper classical turning point - uctp)
