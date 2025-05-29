```
InfinitePartitionFunction(
    [f=randn, T=ComplexF64,] Pspace::S, Nspace::S, [Espace::S]; unitcell=(1,1)
) where {S<:ElementarySpaceLike}
```

Create an InfinitePartitionFunction by specifying its physical, north and east spaces and unit cell. Spaces can be specified either via `Int` or via `ElementarySpace`.
