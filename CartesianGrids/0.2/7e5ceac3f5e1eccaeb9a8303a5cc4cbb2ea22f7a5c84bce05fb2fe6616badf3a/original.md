```
RegularizationMatrix(H::Regularize,f::PointData,u::CellData) -> Hmat
```

Construct and store a matrix representation of regularization associated with `H` for data of type `f` to data of type `u`. The resulting matrix `Hmat` can then be used to apply on point data of type `f` to regularize it to grid data of type `u`, using `mul!(u,Hmat,f)`. It can also be used as just `Hmat*f`.

If `H` is a symmetric regularization and interpolation operator, then this actually returns a tuple `Hmat, Emat`, where `Emat` is the interpolation matrix.
