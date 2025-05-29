```
VTKFile
```

読み込まれたVTK XMLファイルに関するすべての関連情報を保持します。

# フィールド

  * `filename`: 読み込まれたVTKファイルの元のパス
  * `xml_file`: XMLファイルを表すオブジェクト
  * `file_type`: 現在サポートされているのは `"UnstructuredGrid"` または `"ImageData"` のみ
  * `version`: VTK XMLファイルフォーマットのバージョン
  * `byte_order`: `LittleEndian` または `BigEndian` であり、現在はシステムと同じでなければなりません
  * `compressor`: 空（圧縮なし）または `vtkZLibDataCompressor` である可能性があります
  * `appended_data`: 追加データがある場合（XMLドキュメントを参照）、データはここに保存され、便利に取得できます（そうでなければ空です）
  * `n_points`: VTKファイル内のポイントの数
  * `n_cells`: VTKファイル内のセルの数
