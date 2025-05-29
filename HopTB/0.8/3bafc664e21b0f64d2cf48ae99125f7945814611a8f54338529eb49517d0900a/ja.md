```julia
TBModel{T=ComplexF64}(lat::AbstractMatrix{Float64}, orbital_positions::AbstractMatrix{Float64};
    isorthogonal::Bool = true) where T <: Number
```

TBModelを構築します。

追加情報はすべて欠落しています。重なり行列は、モデルが直交しているかどうかにかかわらず、R = [0, 0, 0] の場合に自動的に単位行列として設定されます。R = [0, 0, 0] の位置行列の対角要素は `orbital_positions` に設定されます。
