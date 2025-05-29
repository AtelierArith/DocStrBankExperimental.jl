```
make_paraview_collection(; dir=pwd(), pvd_name=nothing, files=nothing, file_extension = ".vts", time = nothing)
```

`*.vtk` ファイルのリストがある場合、このルーチンは Paraview で開くことができる `*.pvd` ファイルを作成します。これは、以前に vtk ファイルを保存したが、コード自体でコレクションとして保存しなかった場合に便利です。

# オプションのオプション

  * `dir`:    `*.vtk` が保存されているディレクトリ。
  * `pvd_name`:  拡張子なしの結果の `*.pvd` ファイルのファイル名; 指定されていない場合は `full_simulation` が使用されます。
  * `files`:  拡張子なしの `*.vtk` ファイルのベクター; 指定されていない場合は、ディレクトリ内のすべての `*.vtk` ファイルが使用されます。
  * `file_extension`:  vtk ファイルのファイル拡張子。デフォルトは `.vts` ですが、すべての `vt*` が機能します。
  * `time`:  タイムステップのベクター; 指定されていない場合は、擬似タイムステップが割り当てられます。
