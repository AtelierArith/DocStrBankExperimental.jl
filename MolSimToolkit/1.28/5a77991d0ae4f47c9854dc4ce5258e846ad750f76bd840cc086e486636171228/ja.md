```
map_fractions(simulation::Simulation; maxframes=nothing)
```

MDLovoFitをトラジェクトリ上で実行し、構造のRMSDが最も低い部分の割合、RMSDが最も高い部分の割合、および全体の構造のRMSDを取得します。

考慮されるのは、タンパク質残基のCA原子のみです。

引数:

  * `simulation` は、システムのトラジェクトリと原子データを持つSimulationオブジェクトです。

キーワード引数:

  * `maxframes=nothing` は、考慮されるフレームの数です。何も指定しない場合、100フレームが考慮されます。すべてのフレームを考慮するには `length(simulation)` に設定します。

## 例

```jldoctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> sim = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> mf = map_fractions(sim)
-------------------------------------------------------------------
MapFractionsResult: Simulation(structure.pdb, trajectory.dcd)

-------------------------------------------------------------------
フィールド: 
- fraction: アライメントに考慮された原子の割合。
- frame_indices: 考慮された各フレームのフレームインデックス。
- rmsd_low: RMSDが最も低い構造部分の割合のRMSD。
- rmsd_high: アライメントに考慮されなかった部分のRMSD。
- rmsd_all: 全体の構造のRMSD。

RMSD-lowが1.0未満の最大割合: 0.79
                                                         2.0: 0.9
                                                         3.0: 0.99
-------------------------------------------------------------------
```
