`FlexMatrix{T}(rows,cols)` creates a new `FlexMatrix` with rows indexed by `rows`, columns indexed by `cols` and all zero entries of type `T` (which is `Number` if omitted).

`FlexMatrix(v::FlexVector)` converts `v` into a one-column `FlexMatrix` whose sole column index is `Int(1)`
