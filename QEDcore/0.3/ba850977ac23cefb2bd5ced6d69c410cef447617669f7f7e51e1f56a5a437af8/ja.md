```
CoordinateSet{N, D<:Tuple}
```

`N` 個の座標を表す具体的な型で、タプル `coords::D` として保存されます。この型は `AbstractCoordinateSet{N}` のサブタイプであり、位相空間レイアウトなどのさまざまな計算で使用するための座標のセットを処理するように設計されています。

# フィールド

  * `coords::D`: 個々の座標を含むタプル。タプルの各要素は、セット内の座標に対応します。

# コンストラクタ

  * `CoordinateSet{N}(coords::D)`: 座標の数 `N` がタプル `coords` の長さと一致する `CoordinateSet` を作成します。一致しない場合、`ArgumentError` がスローされます。
  * `CoordinateSet(coords::D)`: 提供されたタプル `coords` の長さを `N` として自動的に推測します。

# スロー

  * 提供されたタプルの長さが指定された数 `N` と一致しない場合、`ArgumentError` がスローされます。
