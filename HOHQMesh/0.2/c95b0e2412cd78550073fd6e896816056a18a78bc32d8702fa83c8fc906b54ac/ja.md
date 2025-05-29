```
generate_mesh(control_file;
              output_directory="out",
              mesh_filename=nothing, plot_filename=nothing, stats_filename=nothing,
              verbose=false, subdivision_maximum=8)
```

`control_file`に基づいてメッシュを生成し、結果のファイルを`output_directory`に保存します。

メッシュファイル名、プロットファイル名、および統計ファイル名は、キーワード引数`mesh_filename`、`plot_filename`、および`stats_filename`を使用して設定できます。`nothing`に設定した場合、メッシュファイル、プロットファイル、および統計ファイルのファイル名は制御ファイル名から自動的に生成されます。たとえば、`path/to/ControlFile.control`は、出力ファイル`ControlFile.mesh`、`ControlFile.tec`、および`ControlFile.txt`を生成します。

HOHQMeshからの詳細な出力を有効にするには、キーワード引数`verbose`を使用して追加のメッセージやデバッグメッシュ情報を印刷します。

メッシング中に四分木で許可される最大分割数をオーバーライドするには、`subdivision_maximum`の値を調整します。`subdivision_maximum`のデフォルト値は8であり、これは要素が背景グリッドよりも最大で`2^8`倍小さくなることを意味します。注意してください、これを行う前に考えてください！境界曲線、背景グリッドサイズ、局所的な細分化領域の追加、またはそれらの組み合わせを調整することで、分割深さを調整する必要がなくなる場合があります。

この関数は、メッシュを生成する際のHOHQMeshバイナリの`stdout`への出力を返します。
