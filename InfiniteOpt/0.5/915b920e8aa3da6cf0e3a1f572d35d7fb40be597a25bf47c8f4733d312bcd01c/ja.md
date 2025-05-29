```
PointVariableRef <: FiniteRef
```

特定の点で定義された変数のための `DataType`（例：特定のシナリオでの第二段階変数、離散化された時間点での動的変数）。

**フィールド**

  * `model::InfiniteModel`: 無限モデル。
  * `index::PointVariableIndex`: モデル内の変数のインデックス。
