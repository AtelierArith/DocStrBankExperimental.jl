```
is_withheld(p::PointRecord)
is_withheld(points, inds = :)
```

ポイントが*保留*または削除としてマークされているかどうかを確認し、今後の処理でスキップする必要があるかどうかを判断します。

関連情報: [`PointRecord`](@ref), [`classification`](@ref), [`is_key_point`](@ref), [`is_overlap`](@ref), [`is_synthetic`](@ref)
