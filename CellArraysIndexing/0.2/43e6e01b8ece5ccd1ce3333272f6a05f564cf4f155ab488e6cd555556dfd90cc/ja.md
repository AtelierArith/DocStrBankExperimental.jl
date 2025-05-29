```
getcell(A, I)
```

指定されたインデックス `I` から CellArray `A` のセルを取得します。

# 引数

  * `A::CellArray`: セルを取得する CPUCellArray。
  * `I::Vararg{Int, nDim}`: CPUCellArray 内のセルの位置を指定するインデックス。

# 戻り値

  * 指定されたインデックス `I` のセル。
