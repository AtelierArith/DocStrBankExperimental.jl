```
IMERGFinalDY(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path :: AbstractString = homedir(),
) -> npd :: IMERGDaily{ST,DT}
```

`IMERGDaily` データセット `npd` を作成し、日次出力の最終後処理実行からデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード / 分析が始まる日付
  * `stop` : データセットのダウンロード / 分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために `imergfinaldy` フォルダが作成されるディレクトリ、デフォルトは `homedir()` によって呼び出されるホームディレクトリです。

`npd` の以下のフィールドは固定されます：

  * `ID` : imergfinaldy
  * `ID` : 最終 IMERG 日次
  * `doi`   : 10.5067/GPM/IMERGDF/DAY/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGDF.06
  * `fpref` : 3B-DAY.MS.MRG.3IMERG
  * `fsuff` : S000000-E235959.V06.nc4

```
