```
most_representative_structure(simulation::Simulation; atoms = nothing)
```

シミュレーション内で最も代表的な構造を見つけます。最も代表的な構造は、シミュレーションの平均構造に対するRMSDを最小化するものです。平均構造は反復的に定義され、最初にすべてのフレームを最初のフレームに整列させ、その後整列した構造を平均化します。平均に最も類似した構造が特定され、次の反復の基準構造として使用されます。このプロセスは、平均に最も類似した構造が前の反復と同じになるまで繰り返されます。

# 引数

  * `simulation::Simulation`: シミュレーションオブジェクト。
  * `atoms`: 計算に考慮する原子：

      * `atoms` が `nothing` の場合：関数はすべてのアルファ炭素を考慮します（`"protein and name CA"`）。
      * `atoms` が `AbstractVector{<:PDBTools.Atom}` の場合：関数はベクター内の原子を考慮します。
      * `atoms` が `AbstractVector{<:Int}` の場合：関数はベクター内のインデックスを持つ原子を考慮します。
      * `atoms` が `String` の場合：関数は文字列で選択された原子を考慮します。

# 戻り値

  * タプル `(Int, Float64)` で、以下を含みます：

      * 最も代表的な構造のインデックス。
      * 平均構造に対する最も代表的な構造のRMSD。

# 例

```julia-repl
julia> using MolSimToolkit, MolSimToolkit.Testing, PDBTools

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> most_representative_structure(simulation) # atoms == nothing (すべてのアルファ炭素)
(4, 1.1681526249035976)

julia> most_representative_structure(simulation; atoms = "protein and name CA") # atoms は文字列
(4, 1.1681526249035976)

julia> calphas = select(atoms(simulation), "name CA");

julia> most_representative_structure(simulation; atoms = calphas) # atoms は Vector{PDBTools.Atom}
(4, 1.1681526249035976)

julia> ica = PDBTools.index.(calphas)

julia> most_representative_structure(simulation; atoms = ica) # atoms はインデックスのベクター
(4, 1.1681526249035976)
```
