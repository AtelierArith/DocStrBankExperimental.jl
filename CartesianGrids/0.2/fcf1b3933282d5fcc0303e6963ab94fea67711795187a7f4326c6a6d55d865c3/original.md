```
InterpolationMatrix(H::Regularize,u::CellData,f::PointData) -> Emat
```

Construct and store a matrix representation of interpolation associated with `H` for data of type `u` to data of type `f`. The resulting matrix `Emat` can then be used to apply on grid data of type `u` to interpolate it to point data of type `f`, using `mul!(f,Emat,u)`. It can also be used as just `Emat*u`.
