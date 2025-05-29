```julia
TBModel{T=ComplexF64}(lat::AbstractMatrix{Float64}, site_positions::Matrix{Float64},
    orbital_types::Vector{Vector{Int64}}; isspinful::Bool=false, isorthogonal::Bool=true,
    is_canonical_ordered::Bool=false) where T <: Number
```

TBModelを構築します。

重なり行列は、モデルが直交しているかどうかに関わらず、R = [0, 0, 0] の場合に自動的に単位行列として設定されます。R = [0, 0, 0] の位置行列の対角要素は `site_positions` に従って設定されます。
