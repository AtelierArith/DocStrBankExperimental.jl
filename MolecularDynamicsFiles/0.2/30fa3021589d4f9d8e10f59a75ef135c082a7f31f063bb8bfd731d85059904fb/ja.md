```julia
positions(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Float64}}

```

システム内の粒子のスケーリングされていないラップされた位置を返します。

プロパティ `:x`, `:y`, `:z` に対応します。必要に応じて、他の座標表現からの変換を行います。
