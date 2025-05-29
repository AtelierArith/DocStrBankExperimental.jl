```
IMERGEarlyDY(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path :: AbstractString = homedir(),
) -> npd :: IMERGDaily{ST,DT}
```

`IMERGDaily` データセット `npd` を作成し、日次出力のための近リアルタイム早期処理実行からデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード / 分析が始まる日付
  * `stop` : データセットのダウンロード / 分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために `imergearlydy` フォルダが作成されるディレクトリ、デフォルトは `homedir()` によって呼び出されるホームディレクトリです。

`npd` の以下のフィールドは固定されます：

  * `ID` : imergearlydy
  * `name` : Early IMERG Daily
  * `doi` : 10.5067/GPM/IMERGDE/DAY/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGDE.06
  * `fpref` : 3B-DAY-E.MS.MRG.3IMERG
  * `fsuff` : S000000-E235959.V06.nc4

```
