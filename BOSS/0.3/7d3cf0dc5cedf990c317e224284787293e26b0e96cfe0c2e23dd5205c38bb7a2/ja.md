```
augment_dataset!(data::ExperimentDataPost, x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
augment_dataset!(data::ExperimentDataPost, X::AbstractMatrix{<:Real}, Y::AbstractMatrix{<:Real})
```

データセットに1つ（ベクトルとして）または複数（行列として）のデータポイントを追加します。
