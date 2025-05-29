```julia
unwrapped_positions(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Float64}}

```

システム内の粒子のスケールされていないアンラップ位置を返します。

プロパティ `:xu`, `:yu`, `:zu` に対応します。必要に応じて、他の座標表現からの変換を行います。
