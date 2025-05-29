```
localrvec2Global(rvecslocal::Matrix{T}, l2gRot::StaticMatrix{3,3, FT}) where {T<:Number, FT<:Real}
```

計算局部ベクトルで構成された行列 `rvecslocal` が与えられた局所からグローバル座標への回転行列 `l2gRot` の下でのグローバル座標。
