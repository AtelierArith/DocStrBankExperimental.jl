```julia
boxvectors(
    frame::MolecularDynamicsFiles.MDFrame
) -> StaticArraysCore.SMatrix{3, 3, Float64}

```

シミュレーションボックスの基底ベクトルを行列として返します。シミュレーションセルベクトルは列にあります。  
