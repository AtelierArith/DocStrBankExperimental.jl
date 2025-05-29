```
struct GST <: NMEAString
```

位置誤差統計。

# フィールド

  * `system::String`: GNSSシステム識別子（例：GPS、GLONASS、GALILEO、複合）。
  * `time::Float64`: 秒単位の時間。
  * `rms::Float64`: 擬似距離残差のRMS値；RTK（浮動小数点）およびRTK（固定）処理中のキャリア位相残差を含む
  * `semi_major_error::Float64`: 誤差楕円の半長軸1シグマ誤差、メートル単位
  * `semi_minor_error::Float64`: 誤差楕円の半短軸1シグマ誤差、メートル単位
  * `orientation_error::Float64`: 誤差楕円の向き、真北からの度数
  * `latitude_error::Float64`: 緯度1シグマ誤差、メートル単位
  * `longitude_error::Float64`: 経度1シグマ誤差、メートル単位
  * `height_error::Float64`: 高さ1シグマ誤差、メートル単位
  * `valid::Bool`: データの有効性を示すフラグ。

例の文字列: :GPGST,172814.0,0.006,0.023,0.020,273.6,0.023,0.020,0.031*6A
