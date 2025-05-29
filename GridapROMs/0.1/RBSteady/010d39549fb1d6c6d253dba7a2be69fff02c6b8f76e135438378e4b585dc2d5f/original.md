```
galerkin_projection(a::Projection,b::Projection) -> ReducedProjection
galerkin_projection(a::Projection,b::Projection,c::Projection,args...) -> ReducedProjection
```

(Petrov) Galerkin projection of a projection map `b` onto the subspace `a` (row projection) and, if applicable, onto the subspace `c` (column projection)
