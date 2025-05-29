```
t8_forest_vtk_write_file(forest, fileprefix, write_treeid, write_mpirank, write_level, write_element_id, write_ghosts, num_data, data)
```

フォレストを .pvtu ファイル形式で書き込みます。プロセスごとに 1 つの .vtu ファイルとメタ .pvtu ファイルを書き込みます。この関数は ASCII ファイルを書き込み、t8code が「–with-vtk」で構成されていない場合や t8*forest*vtk*write*file*via*API が利用できない場合に使用できます。

# 引数

  * `forest`:[in] フォレスト。
  * `fileprefix`:[in] 出力ファイルのプレフィックス。
  * `write_treeid`:[in] true の場合、各要素のグローバルツリー ID が書き込まれます。
  * `write_mpirank`:[in] true の場合、各要素の mpirank が書き込まれます。
  * `write_level`:[in] true の場合、各要素の細分化レベルが書き込まれます。
  * `write_element_id`:[in] true の場合、各要素のグローバル要素 ID が書き込まれます。
  * `write_ghosts`:[in] true の場合、各プロセスは追加でそのゴースト要素を書き込みます。ゴースト要素の treeid は -1 です。
  * `num_data`:[in] 書き込むユーザー定義の二重値データフィールドの数。
  * `data`:[in] 長さ *num_data* の [`t8_vtk_data_field_t`](@ref) の配列で、要素ごとのユーザー定義データを提供します。スカラーおよびベクトルフィールドが使用される場合、すべてのスカラー フィールドは配列の最初に来る必要があります。

# 戻り値

成功した場合は true、そうでない場合は false（プロセスローカル）。

### プロトタイプ

```c
int t8_forest_vtk_write_file (t8_forest_t forest, const char *fileprefix, const int write_treeid, const int write_mpirank, const int write_level, const int write_element_id, int write_ghosts, const int num_data, t8_vtk_data_field_t *data);
```
