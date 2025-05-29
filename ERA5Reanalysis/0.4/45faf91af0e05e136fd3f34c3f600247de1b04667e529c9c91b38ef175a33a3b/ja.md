```
ERA5Region
```

グリッド化されたERA5データセットの処理に使用される関連する[GeoRegion](https://github.com/JuliaClimate/GeoRegions.jl)プロパティをインポートする構造体です。

`ERA5Region`タイプは以下のフィールドを含みます：

  * `geo` : 地理情報を含む`GeoRegion`
  * `ID` : `GeoRegion`を指定するために使用されるID
  * `resolution` : ダウンロード/分析されるグリッドデータの解像度
  * `string` : フォルダーとファイル名の仕様、主にバックエンド使用のため
  * `isglb` : ブール値、地球全体にまたがる場合はtrue、そうでない場合はfalse
  * `is360` : 360ºの経度にまたがる場合はtrue
