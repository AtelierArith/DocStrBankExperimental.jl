```
get_line(x1::Real, y1::Real, x2::Real, y2::Real)
```

点 `(x1, y1)` と `(x2, y2)` を通る直線を表す新しい無限の `BoundedQuadratic` を構築します。

# 例

```jldoctest
julia> line = get_line(1., 2., 3., 4.)
BoundedQuadratic: f(x) = + 1.00000 x + 1.00000, ∀x ∈ ℝ

```
