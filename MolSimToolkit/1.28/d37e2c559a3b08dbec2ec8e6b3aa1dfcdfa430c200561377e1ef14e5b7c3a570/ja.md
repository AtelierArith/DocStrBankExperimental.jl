```
center_of_mass(
    indices::AbstractVector{Int};
    simulation::Simulation,
    positions::FramePositions,
    iref::Union{Nothing,Int} = max(1, div(length(indices),2)),
)
```

シミュレーション内の原子の選択の質量中心を、位置に基づいて計算します。選択は `indices` ベクターによって定義され、これは原子のインデックスです。

`iref` パラメータは参照原子のインデックスです。質量中心は、まずこの原子に対してすべての原子の最小画像を計算することによって求められます。デフォルトでは、`indices` ベクターの中央に最も近い原子です。`iref` が `nothing` の場合、座標をラップせずに質量中心が計算されます。

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using PDBTools 

julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> protein_indices = findall(sel"protein", atoms(simulation));

julia> first_frame!(simulation); # シミュレーションを最初のフレームに移動

julia> coor = positions(current_frame(simulation));

julia> cm = center_of_mass(protein_indices, simulation, coor)
3-element Point3D{Float64} with indices SOneTo(3):
 -3.7290442807974906
 -1.5339226637687564
  1.960640754560446
```

!!! compat
    `iref=nothing` オプションはバージョン 1.22.0 で追加されました。

