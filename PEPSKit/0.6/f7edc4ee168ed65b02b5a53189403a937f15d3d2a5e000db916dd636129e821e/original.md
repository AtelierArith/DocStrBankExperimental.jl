```
InfiniteWeightPEPS([f=randn, T=ComplexF64,] Pspace::S, Nspace::S, Espace::S=Nspace; unitcell::Tuple{Int,Int}=(1, 1)) where {S<:ElementarySpace}
```

Create an InfiniteWeightPEPS by specifying its physical, north and east spaces (as `ElementarySpace`s) and unit cell size. Use `T` to specify the element type of the vertex tensors.  Bond weights are initialized as identity matrices of element type `Float64`. 
