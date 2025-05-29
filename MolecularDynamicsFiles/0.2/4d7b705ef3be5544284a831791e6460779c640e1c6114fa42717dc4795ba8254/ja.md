```julia
extra_scalars(
    frame::MolecularDynamicsFiles.MDFrame
) -> Dict{Symbol, Vector}

```

粒子の追加スカラー特性を返します。

特性は、他のMDFrameメソッドがその特性を返さない場合に「追加」と見なされます。「追加」と見なされない特性は次のとおりです: `:id`, `:mol`, `:type`, `:x`, `:y`, `:z`, `:xs`, `:ys`, `:zs`, `:xu`, `:yu`, `:zu`, `:xsu`, `:ysu`, `:zsu`, `:ix`, `:iy`, `:iz`, `:vx`, `:vy`, `:vz`, `:element`, `:mass`
