```
coordination_number(
    sim::Simulation,
    solute::AbstractVector{<:PDBTools.Atom},
    solvent::AbstractVector{<:PDBTools.Atom};
    solvent_natomspermol::Integer,
    cutoff::Real,
    show_progress::Bool = true
)
```

溶質原子と溶媒原子の配位数を計算します。

!!! note
    考慮される距離は、溶質原子と各溶媒分子の原子との**最小距離**です。


# 位置引数

  * `sim::Simulation`: シミュレーションオブジェクト。
  * `solute::AbstractVector{<:PDBTools.Atom}`: 溶質原子のベクター。
  * `solvent::AbstractVector{<:PDBTools.Atom}`: 溶媒原子のベクター。

# キーワード引数

  * `solvent_natomspermol::Integer`: 溶媒分子あたりの原子数。
  * `cutoff::Real`: カットオフ距離。
  * `show_progress::Bool`: 進行状況バーを表示します。（オプション、デフォルト: `true`）

# 戻り値

  * `cn::Vector{Int}`: 各フレームにおける溶質原子と溶媒原子の配位数を持つベクター。

# 例

```jldoctest
julia> using MolSimToolkit, PDBTools, MolSimToolkit.Testing

julia> sim = Simulation(Testing.namd2_pdb, Testing.namd2_traj; frames=1:5);

julia> protein = select(atoms(sim), "protein");

julia> tmao = select(atoms(sim), "resname TMAO");

julia> coordination_number(sim, protein, tmao; solvent_natomspermol=14, cutoff=3.0, show_progress=false)
5-element Vector{Int64}:
 7
 3
 4
 5
 6

```
