```
MDLovoFitResult
```

`mdlovofit` 関数の出力を格納するデータ構造。

フィールド:

  * `simulation`: システムの軌道と原子データを持つシミュレーションオブジェクト。
  * `frame_indices`: 各フレームのフレームインデックスを持つベクター。
  * `rmsd_low`: 最も低いRMSDを持つ構造の割合のRMSD。
  * `rmsd_high`: 最も高いRMSDを持つ構造の割合のRMSD。
  * `rmsd_all`: 全体の構造のRMSD。
  * `rmsf`: 残基または原子インデックスの関数としてのRMSF。
  * `rmsf_file`: RMSFデータを含むファイルの名前。
  * `rmsd_file`: RMSDデータを含むファイルの名前。
  * `aligned_pdb`: 整列された構造を持つPDBファイルの名前。
