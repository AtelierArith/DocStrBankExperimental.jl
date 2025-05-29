```
calculate_feature_importance(method::Function, X::DataFrame, y::Vector)
```

`method`によって定義された特徴量の重要性を計算します。`select_features`と同様に、`X`は`DataFrame`として受け取ることも、`Matrix`の`X_data`と`Vector`の`X_features`に分割して受け取ることもできます。

この関数は、特徴名をキー、スコアを値とする`Dict`を返します。
