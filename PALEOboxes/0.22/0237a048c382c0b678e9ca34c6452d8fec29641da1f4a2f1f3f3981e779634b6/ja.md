```
CellRange <: AbstractCellRange
```

指定された [`Domain`](@ref) 内のセルの範囲を線形リストとして定義します。

# フィールド

  * `domain`
  * `operatorID`
  * `indices`: 有効なJuliaインデックス範囲のものであれば何でも可 eg 1:100, [1 2 3 4], など
