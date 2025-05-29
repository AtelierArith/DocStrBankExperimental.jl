```
is_key_point(p::PointRecord)
is_key_point(points, inds = :)
```

ポイントがポイント密度を減少させる際に削除されるべきでない*キーポイント*としてマークされているかどうかを確認します。

関連情報: [`PointRecord`](@ref), [`classification`](@ref), [`is_overlap`](@ref), [`is_synthetic`](@ref), [`is_withheld`](@ref)
