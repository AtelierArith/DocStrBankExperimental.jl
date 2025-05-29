```
predict(model::Model, inputs::AbstractMatrix)
predict(model::Model, inputs::AbstractVector{<:AbstractVector})
```

提供された `inputs` のコレクションと [`Model`](@ref) に対する予測ターゲット。

`predict_input_type(model)` が [`PointPredictInput`](@ref) である [`Model`](@ref) のサブタイプは、`AbstractMatrix` の入力に対して動作する `predict` 関数を実装する必要があります。

`estimate_type(model)` が [`PointEstimate`](@ref) の場合、この関数は各列に単一の入力の予測を含む別の `AbstractMatrix` を返すべきです。

`estimate_type(model)` が [`DistributionEstimate`](@ref) の場合、この関数は `AbstractVector{<:Distribution}` を返すべきです。
