```
SemiInfiniteVariableRef <: DispatchVariableRef
```

部分的に転写された無限次元変数参照のための `DataType` です。これは、測定によって完全に転写されていない無限の変数を含む測定を拡張するために使用されます。

**フィールド**

  * `model::InfiniteModel`: 無限モデル。
  * `index::SemiInfiniteVariableIndex`: モデル内の変数のインデックス。
