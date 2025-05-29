```julia
particle_types(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{Int64}

```

粒子の種類を返します。

プロパティ `:type` に対応します。フレームに粒子の種類データがない場合、1) 粒子の元素 2) 粒子の質量 から生成しようとします。
