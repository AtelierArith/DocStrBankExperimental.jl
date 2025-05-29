```
surfacepotential(points,normals,topology,μ,ψ0::Function)
```

Returns a surface field for a given shape defined by a triangular mesh with `points`, `normals` and `topology` and for a boundary conditions where ∇ψ has a jump in th e normal direction charectarized with μ and for the external free field given by a potential ψ0.
