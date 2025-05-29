```
is_left_to_right(p::PointRecord)
is_left_to_right(points, inds = :)
```

ポイントが記録されたときに、スキャナーミラーがトラック方向（スキャン角度の増加）に対して左から右に移動していたかどうかを確認します。

関連情報: [`PointRecord`](@ref), [`scan_angle`](@ref), [`is_right_to_left`](@ref), [`is_edge_of_line`](@ref)
