function unitdims(A::AbstractUnitfulVecOrMat) = dims(A)

```
タプルを返す -> (unitrange, unitdomain)

UnitfulMatrixの場合、単位情報が `dims` 関数を上書きします。
```
