```
box(bbox::BoundingBox;
    action   = :none,
    vertices = false)
box(bbox::BoundingBox, action::Symbol;
    vertices=false)
```

`bbox`の境界を使用してボックスを定義します。

`vertices = true`を使用すると、4つのコーナーポイントの配列が返されます：左下、左上、右上、右下。
