```julia
struct RigidTransform{T<:Real}
```

特定の回転中心の周りの単一の回転と平行移動によって表される剛体変換。

# コンストラクタ

```julia
RigidTransform(r::RotMatrix3{T}, t::Vector3{T}, center::Vector3{T} = zeros(Vector3{T}))
RigidTransform(r::Matrix3{T}, t::Vector3{T}, center::Vector3{T} = zeros(Vector3{T}))
```

与えられた回転 `r`、回転の中心 `center`、および平行移動 `t` から新しい `RigidTransform{T}` を作成します。

!!! note
    Rotations.jl のドキュメントから：

    > 与えられた `Matrix3{T}` は `I =RR^T` の性質を持つべきですが、これはコンストラクタによって強制されていません。

