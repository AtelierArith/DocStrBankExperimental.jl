```
Domain2D{BCX, BCY, BCZ}(size::SVector{2, Float64})
Domain2D{BCX, BCY, BCZ}(w, h)
Domain2D(args; [boundaries = (BCX, BCY, BCZ)])
```

`SA[w, h]`の寸法を持つ二次元の長方形ドメインを作成します。

`Domain2D`は、二次元の境界条件を表す二つの[`Boundary`](@ref)タイプによってパラメータ化されています。

参照: [`Domain3D`]
