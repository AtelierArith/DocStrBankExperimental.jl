```julia
mutable struct RigidBody{T}
```

変形しない物体。

`RigidBody`は慣性（[`SpatialInertia`](@ref)として表される）を持ちますが、ルート（ワールド）ボディを表す場合は除きます。`RigidBody`はさらに、それに剛体的に取り付けられた座標系の定義のリストを保存します。
