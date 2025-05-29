```
G = gdalgrid(indata, method::StrSymb="", options=String[]; dest="/vsimem/tmp", kw...)
```

### パラメータ

  * `indata`: ソースデータセット。ファイル名、GMTdataset、Mx3行列、またはGDALデータセットであることができます。
  * `method`: 補間方法の名前。"invdist"、"invdistnn"、"average"、"nearest"、"linear"、"minimum"、"maximum"、"range"、"count"、"average*distance"、"average*distance_pts"のいずれかです。
  * `options`: オプションのリスト。受け入れられるオプションはgdal_gridユーティリティのものです。このリストは文字列のベクトルの形、または単一の文字列に結合された形で指定できます。
  * `kwargs`: `kwargs`にはGMT領域（-R）、inc（-I）、および`save=fname`オプションも含めることができます。

### 戻り値

GMTgridまたはGDALデータセット（ファイルがディスクに書き込まれた場合は何も返されません）。GDALデータセットの返却を強制するには、オプション`gdataset=true`を使用します。
