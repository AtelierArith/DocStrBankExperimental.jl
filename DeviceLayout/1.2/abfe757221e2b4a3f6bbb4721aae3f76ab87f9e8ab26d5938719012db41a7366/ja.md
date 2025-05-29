```
HandedPointHook{T} <: Hook{T}
    h::PointHook{T}
    right_handed::Bool
```

ハンデッドポイントフックを持つ `PointHook`。

1つの `PointHook` を別のものに融合させるために使用される平行移動と回転に加えて、別の `HandedPointHook` に融合される `HandedPointHook` は、そのハンデッドネスに一致させるために必要に応じて反射を適用します。
