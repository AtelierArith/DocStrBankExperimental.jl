```
InfiniteVariableRef <: DispatchVariableRef
```

未転写の無限次元変数参照（例：第二段階変数、時間依存変数）のための `DataType`。

**フィールド**

  * `model::InfiniteModel`: 無限モデル。
  * `index::InfiniteVariableIndex`: モデル内の変数のインデックス。
