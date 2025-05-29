```
get_XYZ20(xyz_h5::String;
          info::String  = splitpath(xyz_h5)[end],
          tt_sort::Bool = true,
          silent::Bool  = false)
```

HDF5ファイルから`XYZ20`フライトデータを取得します。2020年のSGLデータフィールドに基づいています。

**引数:**

  * `xyz_h5`:  フライトデータHDF5ファイルのパス/名前（`.h5`拡張子はオプション）
  * `info`:    （オプション）フライトデータ情報
  * `tt_sort`: （オプション）trueの場合、データを時間でソートします（行ではなく）
  * `silent`:  （オプション）trueの場合、出力はありません

**戻り値:**

  * `xyz`: `XYZ20`フライトデータ構造体
