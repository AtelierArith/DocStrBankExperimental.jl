```
set_vars!(model::AbstractFluxNLPModel{T,S}, new_w::AbstractVector{T}) where {T<:Number, S}
```

変数を設定し、チェーンを再構築します。
