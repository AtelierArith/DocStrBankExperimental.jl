```
coordinate_names(coord_set::AbstractCoordinateSet)
```

与えられた座標セット内のすべての座標の名前を取得します。

# 引数

  * `coord_set::AbstractCoordinateSet`: 複数の座標を格納するコンテナである座標セット。

# 戻り値

  * 各文字列がセット内の座標の名前であり、利用可能な場合はその粒子インデックスを含む文字列のタプル。

この関数は通常、`AbstractCoordinateSet`のサブタイプに対して実装され、人間が読みやすい形式でセット内の各座標の名前を返すために使用されます。
