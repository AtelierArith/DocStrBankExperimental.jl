```
bulk_coordination(
    simulation::Simulation;
    reference_solute::AbstractVector{<:PDBTools.Atom}, 
    solute::AbstractVector{<:PDBTools.Atom},
    n_atoms_per_molecule_solute::Integer,
    solvent::AbstractVector{<:PDBTools.Atom}, 
    n_atoms_per_molecule_solvent::Integer,
    dmax::Real = 5.0,
    cutoff::Real = 20.0,
    bin_size::Real = 0.1,
    show_progress = true,
)
```

ある種類の溶媒分子の配位数を、参照溶質分子までの距離の関数として計算します。

例えば、タンパク質が水とTMAOの混合物で溶媒和されていると想像してください。この関数は、タンパク質までの距離の関数として、TMAO分子に対して与えられた距離内にある水分子の数を計算することを可能にします。つまり、タンパク質までの距離の関数として、TMAOに対する水の配位数を計算します。

この関数は、距離と配位数のヒストグラムを距離の関数として返します。

!!! compat
    この関数は、MolSimToolkit.jlのバージョン1.11.0で導入されました。


# 引数

  * `simulation::Simulation`: シミュレーションオブジェクト
  * `reference_solute::AbstractVector{PDBTools.Atom}`: 参照溶質分子の原子（上記の例ではタンパク質）。
  * `solute::AbstractVector{PDBTools.Atom}`: 溶質分子の原子（上記の例ではTMAO）。
  * `n_atoms_per_molecule_solute::Integer`: 溶質の分子あたりの原子数。
  * `solvent::AbstractVector{PDBTools.Atom}`: 溶媒分子の原子（上記の例では水）。
  * `n_atoms_per_molecule_solvent::Integer`: 溶媒の分子あたりの原子数。
  * `dmax::Real = 5.0`: 溶質に対して溶媒分子を配位と見なすための最大距離。
  * `cutoff::Real = 20.0`: ヒストグラムを計算するための参照分子までの最大距離。
  * `bin_size::Real = 0.1`: ヒストグラムのビンのサイズ。
  * `show_progress = true`: 進行状況バーを表示するかどうか。

# 例

```julia-repl
julia> using MolSimToolkit, PDBTools

julia> pdb = readPDB(MolSimToolkit.Testing.namd2_pdb); # タンパク質-TMAO-水システム

julia> trajectory = MolSimToolkit.Testing.namd2_traj;

julia> simulation = Simulation(pdb, trajectory)
Simulation 
    Atom type: Atom
    PDB file: -
    Trajectory file: /home/leandro/.julia/dev/MolSimToolkit/test/data/namd/protein_in_water_tmao/trajectory.dcd
    Total number of frames: 20
    Frame range: 1:1:20
    Number of frames in range: 20
    Current frame: nothing

julia> r, h = bulk_coordination(
           simulation;
           reference_solute = select(pdb, "protein"),
           solute = select(pdb, "resname TMAO"),
           n_atoms_per_molecule_solute = 14,
           solvent = select(pdb, "water"),
           n_atoms_per_molecule_solvent = 3,
       );

julia> using Plots

julia> plot(r, h, # `r`の関数として`h`をプロット
           xlabel = "タンパク質までの距離 (Å)",
           ylabel = "TMAO-水 配位数",
           linewidth=2,
           label=:none, framestyle=:box, fontfamily="Computer Modern",
       )
```
