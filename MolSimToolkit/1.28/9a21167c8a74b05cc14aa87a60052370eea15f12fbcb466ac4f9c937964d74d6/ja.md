```
average_dihedrals(sim::Simulation, v::AbstractVector{<:AbstractVector{<:Integer}}; degrees=true)
average_dihedrals(sim::Simulation, v::AbstractVector{<:AbstractVector{<:PDBTools.Atom}}; degrees=true)
```

多くの4つのベクトルのセットに対する平均二面角を計算します。入力は、二面角を形成する原子のインデックスを含むベクトルのベクトル、または`PDBTools.Atom`オブジェクトです。

この関数は、ラジアンまたは度での平均二面角を含むベクトルを返します。

## 例

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using MolSimToolkit, MolSimToolkit.Testing, PDBTools

julia> atoms = read_pdb(Testing.namd2_pdb);

julia> cAs = select(atoms, "name CA and residue < 5"); # 4原子

julia> r1b = select(atoms, "residue 1 and backbone"); # 4原子

julia> inds = [ index.(cAs), index.(r1b) ]; # インデックスのベクトルのリスト

julia> sim = Simulation(Testing.namd2_pdb, Testing.namd2_traj);

julia> ds = average_dihedrals(sim, inds)
2-element Vector{Float64}:
 -60.12860673875001
  -0.3398274578758668

julia> ats = [ cAs, r1b ]; # PDBTools.Atomのベクトルのリスト

julia> ds = average_dihedrals(sim, ats)
2-element Vector{Float64}:
 -60.12860673875001
  -0.3398274578758668

```
