```
apply_rhs!(data::RHSData, f::AbstractVector, ch::ConstraintHandler, applyzero::Bool=false)
```

剛性行列を変更することなく、右辺ベクトルに境界条件を適用します。

関連情報: [`get_rhs_data`](@ref).
