```
rotation(destination::AbstractVector{<:Number}; kwargs...) -> SMatrix{3, 3}
rotation(destination::Tuple{Number, Number}; unit::Symbol=:radian) -> SMatrix{3, 3}
```

`[0, 0, 1]`を`destination`ベクトルの方向に回転させる回転行列を取得します。
