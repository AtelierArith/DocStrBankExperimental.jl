```
normalderivatives(points,normals,topology,P∇ψ,μ,∇ψ0::Function; eps=0.0001, NP=100)
```

Calculates ∇ψ.n approached to the object surface from *interior* region. To use the function surface properties `points`, `normals` and `topology` are required. To use the function it is required to have a tangential field components (see `tangentialderivatives` and `surfacepotential`), boundary jump condition μ and a gradient of external free field. 
