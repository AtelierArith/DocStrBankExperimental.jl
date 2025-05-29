```
PVTKFile
```

読み込まれたParallel VTK XMLファイルに関するすべての関連情報を保持します。

# フィールド

  * `filename`: 読み込まれたPVTKファイルの元のパス
  * `xml_file`: xml情報
  * `file_type`: 現在サポートされているのは `"PRectilinearGrid"` または `"PImageData"` のみ
  * `version`: VTK XMLファイルフォーマットのバージョン
  * `vtk_filenames`: 各並列ファイルのファイル名を含む文字列のベクター
  * `vtk_files`: 各ファイルに関する情報を含む `VTKFile` データのベクター
