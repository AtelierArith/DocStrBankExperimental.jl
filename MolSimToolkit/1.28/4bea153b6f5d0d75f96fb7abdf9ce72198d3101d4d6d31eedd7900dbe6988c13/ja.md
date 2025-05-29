```
MapFractionsResult
```

`map_fractions` 関数の出力を格納するデータ構造。

フィールド:

  * `simulation` は、システムの軌道と原子データを持つ Simulation オブジェクトです。
  * `frame_indices` は、考慮された各フレームのフレームインデックスを含みます。
  * `fraction` は、アライメントで考慮された原子の割合を含みます。
  * `rmsd_low` は、最も低い RMSD を持つ構造の割合の RMSD を含みます。
  * `rmsd_high` は、アライメントのために考慮されなかった割合の RMSD を含みます。
  * `rmsd_all` は、全体の構造の RMSD を含みます。
