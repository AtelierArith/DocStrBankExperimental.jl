```
ss_map(
    simulation::Simulation; 
    selection::Union{AbstractString,Function}=PDBTools.isprotein,
    ss_method=stride_run,
    show_progress=true
)
```

軌道の二次構造マップを計算します。各行が残基で、各列がフレームである二次構造コードの行列を返します。

デフォルトでは、すべてのタンパク質原子が考慮されます。`selection`キーワード引数を使用して、異なる選択を選ぶことができます。例えば、`selection="protein and chain A"`のように`PDBTools`の選択構文を使用することができます。また、`selection=at -> chain(at) in ('A', 'B')`のように一般的なJulia関数を使用することもできます。

`ss_method`キーワード引数を使用して、二次構造予測方法を選択できます。これは`stride_run`または`dssp_run`のいずれかです。デフォルトは`stride_run`です。STRIDEはより高速なアルゴリズムであり、DSSPはPDBデータベースのデフォルトのものです。

`show_progress`キーワード引数は、進行状況バーが表示されるかどうかを制御します。

クラスについては、ProteinSecondaryStructures.jlパッケージのドキュメントを参照してください。

## 例

```jldoctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> ssmap = ss_map(simulation; selection="residue >= 30 and residue <= 35", show_progress=false)
6×5 Matrix{Int64}:
 5  9  5  5  5
 5  9  5  5  5
 5  1  5  5  5
 5  1  5  5  5
 5  1  5  5  5
 9  9  9  9  9

julia> ss_name.(ssmap)
6×5 Matrix{String}:
 "turn"  "coil"       "turn"  "turn"  "turn"
 "turn"  "coil"       "turn"  "turn"  "turn"
 "turn"  "310 helix"  "turn"  "turn"  "turn"
 "turn"  "310 helix"  "turn"  "turn"  "turn"
 "turn"  "310 helix"  "turn"  "turn"  "turn"
 "coil"  "coil"       "coil"  "coil"  "coil"

```
