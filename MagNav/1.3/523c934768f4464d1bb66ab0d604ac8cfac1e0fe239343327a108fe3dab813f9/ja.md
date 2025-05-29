```
get_XYZ20(xyz_160_h5::String, xyz_h5::String;
          info::String = splitpath(xyz_160_h5)[end] * " & " * splitpath(xyz_h5)[end],
          silent::Bool = false)
```

保存されたHDF5ファイルから160 Hz（部分的）`XYZ20`フライトデータを取得し、別の保存されたHDF5ファイルから10 Hz `XYZ20`フライトデータと結合します。データは時間順にソートされており、データが整列されることを保証します。

**引数:**

  * `xyz_160_h5`: 160 HzフライトデータHDF5ファイルのパス/名前（`.h5`拡張子はオプション）
  * `xyz_h5`:     10 HzフライトデータHDF5ファイルのパス/名前（`.h5`拡張子はオプション）
  * `info`:       （オプション）フライトデータ情報
  * `silent`:     （オプション）trueの場合、出力は表示されません

**戻り値:**

  * `xyz`: `XYZ20`フライトデータ構造体
