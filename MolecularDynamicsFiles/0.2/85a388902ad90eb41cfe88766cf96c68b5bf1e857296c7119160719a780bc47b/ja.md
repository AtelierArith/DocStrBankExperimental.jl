```julia
add_extra_scalar!(
    frame::MolecularDynamicsFiles.MDFrame,
    name::Symbol,
    values::AbstractVector{Float64}
) -> AbstractVector{Float64}

```

追加のスカラー粒子プロパティを追加します。

`name` は `:id`, `:mol`, `:type`, `:x`, `:y`, `:z`, `:xs`, `:ys`, `:zs`, `:xu`, `:yu`, `:zu`, `:xsu`, `:ysu`, `:zsu`, `:ix`, `:iy`, `:iz`, `:vx`, `:vy`, `:vz`, `:element`, `:mass` のいずれでもあってはなりません。 `values` の長さは `length(frame)` と一致している必要があります。 `values[i]` は、粒子の id `id_tags(frame)[i]` の追加されたプロパティの値に対応します。
