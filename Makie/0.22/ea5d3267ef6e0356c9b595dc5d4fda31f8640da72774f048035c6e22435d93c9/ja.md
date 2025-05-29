```
Plane(point::Point, normal::Vec)
Plane(normal::Vec, distance::Real)
```

与えられた `normal` を持ち、指定された `point` を含む Plane を作成します。内部表現は `distance = dot(point, normal)` を使用しており、これも直接構築することができます。
