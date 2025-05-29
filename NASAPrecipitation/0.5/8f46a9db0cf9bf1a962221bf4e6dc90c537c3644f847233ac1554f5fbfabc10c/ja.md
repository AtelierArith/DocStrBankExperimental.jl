```
TRMM3HourlyNRT(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: TRMM3Hourly{ST,DT}
```

`TRMM3Hourly` データセット `npd` を作成し、3時間ごとの出力の近リアルタイム実行からデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード / 分析が始まる日付
  * `stop` : データセットのダウンロード / 分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために `trmm3hourlynrt` フォルダが作成されるディレクトリ、デフォルトは `homedir()` で呼び出されるホームディレクトリです。

`npd` の以下のフィールドは固定されます：

  * `ID` : trmm3hourlynrt
  * `name` : 近リアルタイム TRMM 3時間ごと
  * `doi`   : 10.5067/TRMM/TMPA/3H-E/7
  * `hroot` : https://disc2.gesdisc.eosdis.nasa.gov/opendap/TRMM*RT/TRMM*3B42RT.7
  * `fpref` : 3B42RT
  * `fsuff` : 7R2.nc4

```
