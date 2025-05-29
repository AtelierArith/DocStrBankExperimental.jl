function unitdims(A::AbstractUnitfulVecOrMat) = dims(A)

```
Return tuple -> (unitrange, unitdomain)

for UnitfulMatrix, unit information overrides the `dims` function.
```
