```
PVDFile
```

読み込まれたPVDファイルに関するすべての関連情報を保持します。

# フィールド

  * `filename`: 読み込まれたPVTKファイルの元のパス
  * `file_type`: 現在サポートされているのは `"PRectilinearGrid"` または `"PImageData"` のみ
  * `vtk_filenames`: 各ファイルのファイル名を含む文字列のベクター
  * `directories`: 各ファイルのディレクトリを含む文字列のベクター
  * `timestep`: 各ファイルの時間を含む `Float64` のベクター
