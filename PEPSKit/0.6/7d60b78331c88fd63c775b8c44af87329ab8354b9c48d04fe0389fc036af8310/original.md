```
InfinitePEPS([f=randn, T=ComplexF64,] Pspaces::A, Nspaces::A, [Espaces::A]) where {A<:AbstractMatrix{<:Union{Int,ElementarySpace}}}
```

Create an `InfinitePEPS` by specifying the physical, north virtual and east virtual spaces of the PEPS tensor at each site in the unit cell as a matrix. Each individual space can be specified as either an `Int` or an `ElementarySpace`.
