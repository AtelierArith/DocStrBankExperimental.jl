```
trixi2vtk(filename::AbstractString...;
          format=:vtu, verbose=false, hide_progress=false, pvd=nothing,
          output_directory=".", nvisnodes=nothing, save_celldata=true,
          reinterpolate=true, data_is_uniform=false)
```

Trixiによって生成された出力ファイルをVTKファイル（VTUまたはVTI）に変換します。

# 引数

  * `filename`: VTKファイルに変換する1つ以上のTrixiソリューション/再起動/メッシュファイル。             ファイル名はファイルグロビングをサポートしており、例えば「solution*」は             `solution`で始まるすべてのファイルにマッチします。
  * `format`: ソリューション/再起動ファイルの出力形式。'vtu'または'vti'を指定できます。
  * `verbose`: `true`に設定すると詳細な出力が有効になります。
  * `hide_progress`: 進行状況バーを非表示にします（`verbose`が`true`の場合は自動的に非表示になります）。
  * `pvd`: PVDファイルを保存するためにこのファイル名を使用します（自動検出名の代わりに）。        名前のみが使用されることに注意してください（ディレクトリとファイル拡張子は無視されます）。
  * `output_directory`: 生成されたファイルが保存される出力ディレクトリ。
  * `nvisnodes`: 要素ごとの視覚化ノードの数。              （デフォルト: StructuredMeshまたはUnstructuredMesh2DのDGノードの数、                        TreeMeshの場合はDGノードの数の2倍）。              `0`（ゼロ）の値はDG要素のノード数を使用します。
  * `save_celldata`: セルベースのデータを保存するかどうかを決定するブール値。                  （デフォルト: `true`）
  * `reinterpolate`: データを均一な点に再補間するかどうかを決定するブール値。                  `false`の場合、計算ノードの生データが適切な形式にコピーされます。                  （デフォルト: `true`）
  * `data_is_uniform`: 変換されるデータが均一な点の格子上の有限差分法からのものであるかどうかを示すブール値。                    （デフォルト: `false`）

# 例

```julia
julia> trixi2vtk("out/solution_000*.h5")
[...]
```
