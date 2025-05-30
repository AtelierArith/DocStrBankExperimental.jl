```
CellRangeColumns <: AbstractCellRange
```

指定された [`Domain`](@ref) 内のセルの範囲を定義し、`columns` によって整理されます。

# フィールド

  * `domain`
  * `operatorID`
  * `indices`: 任意の順序で全てのセルを反復するイテレータ
  * `columns`: 列を反復するイテレータ: columns[n] は、セルが上から下に順序付けられた Pair icol=>cells を返します
