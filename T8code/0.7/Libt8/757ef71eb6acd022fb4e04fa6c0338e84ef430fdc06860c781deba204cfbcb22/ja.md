```
t8_forest_vtk_write_file_via_API(forest, fileprefix, write_treeid, write_mpirank, write_level, write_element_id, curved_flag, write_ghosts, num_data, data)
```

フォレストを .pvtu ファイル形式で書き込みます。プロセスごとに 1 つの .vtu ファイルとメタ .pvtu ファイルを書き込みます。この関数は vtk ライブラリを使用します。t8code は使用するために "–with-vtk" で構成されている必要があります。現在、ピラミッド要素はサポートされていません。

!!! note
    t8code が vtk で構成されていない場合は、t8*forest*vtk*write*file を使用してください。


# 引数

  * `forest`:[in] フォレスト。
  * `fileprefix`:[in] 出力ファイルのプレフィックス。メタファイルは *fileprefix*.pvtu という名前になります。
  * `write_treeid`:[in] true の場合、各要素のグローバルツリー ID が書き込まれます。
  * `write_mpirank`:[in] true の場合、各要素の mpirank が書き込まれます。
  * `write_level`:[in] true の場合、各要素の細分化レベルが書き込まれます。
  * `write_element_id`:[in] true の場合、各要素のグローバル要素 ID が書き込まれます。
  * `curved_flag`:[in] true の場合、要素を vtk の曲線要素タイプとして書き込みます。
  * `write_ghosts`:[in] true の場合、ゴースト要素も書き出します。
  * `num_data`:[in] 書き込むユーザー定義の二重値データフィールドの数。
  * `data`:[in] ユーザー定義の要素ごとのデータを提供する長さ *num_data* の [`t8_vtk_data_field_t`](@ref) の配列。スカラーおよびベクトルフィールドが使用される場合、すべてのスカラー フィールドは配列の最初に来る必要があります。

# 戻り値

成功した場合は true、そうでない場合は false（プロセスローカル）。

### プロトタイプ

```c
int t8_forest_vtk_write_file_via_API (t8_forest_t forest, const char *fileprefix, const int write_treeid, const int write_mpirank, const int write_level, const int write_element_id, const int curved_flag, const int write_ghosts, const int num_data, t8_vtk_data_field_t *data);
```
