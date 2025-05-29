```
path2kml(path::Path,
         path_kml::String = "path.kml";
         width::Int       = 3,
         color1::String   = "",
         color2::String   = "00ffffff",
         points::Bool     = false)
```

Google Earthで使用するフライトパスのKMLファイルを作成します。

**引数:**

  * `path`:      `Path`構造体、すなわち`Traj`軌道構造体、`INS`慣性航法システム構造体、または`FILTout`フィルタ抽出出力構造体
  * `path_kml`:  （オプション）保存するフライトパスKMLファイルのパス/名前（`.kml`拡張子はオプション）
  * `width`:     （オプション）線の幅
  * `color1`:    （オプション）パスの色
  * `color2`:    （オプション）パスの下の色
  * `points`:    （オプション）trueの場合、線の代わりにポイントを作成

**戻り値:**

  * `nothing`: `path_kml`が作成されます
