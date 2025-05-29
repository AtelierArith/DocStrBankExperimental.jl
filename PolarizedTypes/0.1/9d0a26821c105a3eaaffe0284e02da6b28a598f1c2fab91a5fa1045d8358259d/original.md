```
basis_transform([T=Float64,], b1::PolBasis, b2::PolBasis)
basis_transform([T=Float64,], b1::PolBasis=>b2::PolBasis)
```

Produces the transformation matrix that transforms the vector components from basis `b1` to basis `b2`. This means that if for example `E` is the circular basis then `basis_transform(CirBasis=>LinBasis)E` is in the linear basis. In other words the **columns** of the transformation matrix are the coordinate vectors of the new basis vectors in the old basis.

# Example

```julia-repl
julia> basis_transform(CirBasis()=>LinBasis())
2×2 StaticArraysCore.SMatrix{2, 2, ComplexF64, 4} with indices SOneTo(2)×SOneTo(2):
 0.707107-0.0im       0.707107-0.0im
      0.0-0.707107im       0.0+0.707107im
```
