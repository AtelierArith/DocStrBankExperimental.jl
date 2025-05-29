```
gdalread(fname::AbstractString, opts=String[]; gdataset=false, kwargs...)
```

ディスクファイルからラスタまたはベクタファイルを読み込み、結果をGMTタイプ（デフォルト）またはGDALデータセットとして返します。

  * `fname`: 入力データ。ファイル名、GMTgridまたはGMTimageオブジェクト、またはGDALデータセットであることができます。
  * `opts`: オプションのリスト。受け入れられるオプションはgdal_translateユーティリティのものです。このリストは文字列のベクタの形、または単一の文字列に結合された形で指定できます。
  * `gdataset`: `true`に設定すると、GMTタイプの代わりにGDALデータセットを返すよう強制します。
  * `kwargs`: このオプションはGMT領域（-R）およびインクリメント（-I）を受け入れます。

### 戻り値

GMTグリッド/画像またはGDALデータセット
