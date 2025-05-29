```
compatible(psos::AbstractVector{PSOModel{T, U}}) where {T, U}
compatible(bboxes::AbstractVector{Blackbox{T, U}}) where {T, U}
```

モデルがカスケードできるかどうかを確認します。PSOModelsの場合は常に真であり、同じ値の`ω`を共有するBlackboxesの場合も真です。
