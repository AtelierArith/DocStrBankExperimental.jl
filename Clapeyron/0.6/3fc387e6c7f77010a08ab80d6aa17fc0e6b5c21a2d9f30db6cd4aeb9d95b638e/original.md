```
index_reduction(model::EoSModel,z,zmin = sum(z)*4*eps(eltype(z)))
index_reduction(model::EoSModel,bools <: AbstractVector{Bool})
```

Removes any component with composition `z[i] < zmin`. returns a reduced model `model_r` and a vector of indices `idx_r`, such as:

```julia
model_r,idx_r = index_reduction(model,z)
eos(model,V,T,z) ≈ eos(model_r,V,T,z[idx_r])
```

if the model does not have empty compositions, it will just return the input model.

The function will error if the reduction results in an empty model.

You can pass an arbitrary boolean vector (`bools`) to perform the reduction.
