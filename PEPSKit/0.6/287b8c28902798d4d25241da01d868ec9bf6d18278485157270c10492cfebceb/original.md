```
InfiniteWeightPEPS([f=randn, T=ComplexF64,] Pspaces::M, Nspaces::M, [Espaces::M]) where {M<:AbstractMatrix{<:Union{Int,ElementarySpace}}}
```

Create an InfiniteWeightPEPS by specifying the physical, north virtual and east virtual spaces of the PEPS vertex tensor at each site in the unit cell as a matrix. Each individual space can be specified as either an `Int` or an `ElementarySpace`. Bond weights are initialized as identity matrices of element type `Float64`. 
