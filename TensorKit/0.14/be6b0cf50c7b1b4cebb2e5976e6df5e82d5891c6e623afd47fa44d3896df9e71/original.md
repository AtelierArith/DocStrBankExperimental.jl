```
const Rep
```

A constant of a singleton type used as `Rep[G]` with `G<:Group` a type of group, to construct or obtain the concrete type `GradedSpace{Irrep[G],D}` instances without having to specify `D`. Note that `Rep[G] == Vect[Irrep[G]]`.

See also [`Irrep`](@ref) and [`Vect`](@ref).
