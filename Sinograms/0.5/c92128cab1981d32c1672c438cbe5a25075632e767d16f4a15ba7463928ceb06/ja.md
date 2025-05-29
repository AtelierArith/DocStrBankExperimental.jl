```
parker_weight(rg::CtFan; T::Type{<:AbstractFloat} = Float32, kwargs...)
```

3Dの場合、サイズが次の`Array{T,3}`を返します。

  * `(1,1,1)` 360°の軌道を持つ典型的なファンケース
  * `(ns,1,na)` 短いスキャンを含む非典型的なファンケース
