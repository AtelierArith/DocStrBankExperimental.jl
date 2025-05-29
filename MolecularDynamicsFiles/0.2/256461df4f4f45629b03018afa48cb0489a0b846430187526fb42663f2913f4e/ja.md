```julia
images(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Int16}}

```

システム内の粒子の画像座標を返します。

プロパティ `:ix`, `:iy`, `:iz` に対応します。必要に応じて、展開された座標から画像を生成します。
