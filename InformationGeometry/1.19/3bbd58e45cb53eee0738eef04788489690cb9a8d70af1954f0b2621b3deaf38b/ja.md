```
StructurallyIdentifiable(DM::AbstractDataModel, mle::AbstractVector{<:Number}=MLE(DM); showall::Bool=false, noise::Real=1e-5, thresh::Real=1e-12, N::Int=3)
```

モデルのパラメータに関するヤコビアンの特異値が閾値以下であるかをチェックし、関連する特異方向を提供します。
