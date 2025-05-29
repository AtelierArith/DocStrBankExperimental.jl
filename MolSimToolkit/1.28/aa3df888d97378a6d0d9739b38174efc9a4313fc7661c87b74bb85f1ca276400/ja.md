```
mdlovofit(
    simulation::Simulation; 
    fraction::AbstractFloat, 
    output_name::Union{String,Nothing} = nothing, 
    reference_frame::Int = 1, 
    maxframes=nothing
)
```

MDLovoFitをトラジェクトリに対して実行し、RMSDが最も低い構造の割合に含まれる原子のみを整列させます。考慮されるのは、タンパク質残基のCA原子のみです。

引数:

  * `simulation` は、システムのトラジェクトリと原子データを持つSimulationオブジェクトです。
  * `fraction` は、整列に考慮される原子の割合です。

オプションの引数:

  * `output_name=nothing` は、出力ファイルのベース名です。何も指定しない場合、デフォルトの名前が使用されます。
  * `reference_frame=1` は、整列の基準として使用されるフレームのインデックスです。
  * `maxframes=nothing` は、考慮されるフレームの数です。何も指定しない場合、100フレームが考慮されます。すべてのフレームを考慮するには `length(simulation)` に設定します。

出力:

  * 整列の結果を含む `MDLovoFitResult` データ構造。

および出力ファイル:

  * RMSFデータを含む `output_name_rmsf.dat`。
  * RMSDデータを含む `output_name_rmsd.dat`。
  * 整列された構造を含む `output_name_aligned.pdb`。

## 例

```jldoctest
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> sim = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> md = mdlovofit(sim, fraction=0.7, output_name="mdlovofit_50")
-------------------------------------------------------------------
MDLovoFitResult: Simulation(structure.pdb, trajectory.dcd)

-------------------------------------------------------------------

整列されたpdbファイル: mdlovofit_50_aligned.pdb
RMSFデータファイル: mdlovofit_50_rmsf.dat
RMSDデータファイル: mdlovofit_50_rmsd.dat

考慮されたフレームの数: 5
すべての原子の平均RMSD: 1.79
最も低いRMSDの70.0%の原子の平均RMSD: 0.53
最も高いRMSDの30.0%の原子の平均RMSD: 4.71

フィールドに利用可能なフレームインデックス: frame_indices
フィールドに利用可能なRMSDデータ: rmsd_low, rmsd_high, および rmsd_all

フィールドに利用可能なRMSFデータ: rmsf (原子の数: 43)
-------------------------------------------------------------------
```
