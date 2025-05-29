```
Domain3D{BCX, BCY, BCZ}(size::SVector{3, Float64})
Domain3D{BCX, BCY, BCZ}(w, h, d)
Domain3D(args; [boundaries = (BCX, BCY, BCZ)])
```

三次元の直方体ドメインを次元 `SA[w, h, d]` で作成します。

`Domain3D` は、三次元の境界条件を表す三つの [`Boundary`](@ref) タイプによってパラメータ化されています。

参照: [`Domain2D`]
