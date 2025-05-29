```
rmsd_matrix(
    simulation::Simulation, 
    indices::AbstractVector{<:Integer}; 
    mass::Union{AbstractVector{<:Integer}, Nothing} = nothing,
    align::Bool = true,
    show_progress = true,
)
```

トラジェクトリに沿った原子のセットのRMSD行列を計算します。

`indices`ベクターには考慮すべき原子のインデックスが含まれています。`mass`引数は、原子の質量が異なる場合にその質量を提供するために使用できます。`align`引数は、RMSDを計算する前にフレームを整列させるために使用できます。

`show_progress`引数は、進行状況バーを表示するために使用できます。

# 戻り値

各フレームのペア間のRMSD値を持つ対称行列。たとえば、5つのフレームを持つトラジェクトリでは、行列は5x5の行列で、各フレームの構造間のRMSD値が含まれます。

# 例

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> using PDBTools

julia> atoms = readPDB(Testing.namd_pdb);

julia> cas = findall(Select("name CA"), atoms); # CAインデックス

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> rmsd_matrix(simulation, cas; show_progress=false)
5×5 Matrix{Float64}:
 0.0      2.83887  2.9777   2.46214  3.80357
 2.83887  0.0      2.35492  2.64463  4.68028
 2.9777   2.35492  0.0      2.08246  3.46149
 2.46214  2.64463  2.08246  0.0      2.97835
 3.80357  4.68028  3.46149  2.97835  0.0
```
