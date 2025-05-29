```julia
TBModel{T=ComplexF64}(norbits::Int64, lat::AbstractMatrix{Float64};
    isorthogonal::Bool=true) where T <: Number
```

TBModelを構築します。

重なり行列は、モデルが直交しているかどうかに関わらず、R = [0, 0, 0] の場合は自動的に単位行列として設定されます。すべての追加情報は欠落しています。
