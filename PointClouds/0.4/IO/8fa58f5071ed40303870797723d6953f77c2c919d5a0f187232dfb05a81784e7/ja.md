```
LAS([T,] points; kws...)
```

新しい `LAS` を、タイプ `T <: PointRecord` のポイントで作成します。`points` は `PointRecord` の `AbstractVector` として渡すことも、ポイント属性名に対応するキーと `AbstractVector` の値を持つ `NamedTuple` として渡すこともできます。キーワード引数は `LAS` タイプの対応するフィールドを設定します。
