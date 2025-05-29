```
rmsd(simulation::Simulation, indices::AbstractVector{<:Integer}; mass = nothing, reference_frame = nothing, show_progress = true)
```

2つの点のセット間の二乗平均平方根偏差（RMSD）を、軌道に沿って計算します。

# 引数

  * `indices` ベクトルは考慮すべき原子のインデックスを含みます。
  * `mass` 引数は、原子の質量が異なる場合にその質量を提供するために使用できます。
  * `reference_frame` 引数は、軌道を整列させるための参照フレームを提供するために使用できます：

      * `reference_frame == nothing` の場合、最初のフレームが使用されます（デフォルトの動作）。
      * `reference_frame == :average` の場合、平均構造が使用されます。
      * `reference_frame` が整数の場合、そのインデックスのフレームが参照として使用されます。

# 例

## 軌道に沿った rmsd の計算

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> using PDBTools

julia> atoms = readPDB(Testing.namd_pdb);

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> cas = findall(sel"name CA", atoms); # CA インデックス

julia> rmsd(simulation, cas; show_progress=false)
5-element Vector{Float64}:
 0.0
 2.8388710154609034
 2.9776998440690385
 2.4621444212469483
 3.8035683196100796

julia> rmsd(simulation, cas; reference_frame=:average, show_progress=false)
5-element Vector{Float64}:
 1.8995986972454748
 2.1512244220536973
 1.5081703191869376
 1.1651111324544219
 2.757039151265317
```
