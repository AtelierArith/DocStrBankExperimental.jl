```
TRMMDailyNRT(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: TRMMDaily{ST,DT}
```

`npd`という`TRMMDaily`データセットを作成し、日次出力のための近リアルタイム処理実行からデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード/分析が始まる日付
  * `stop` : データセットのダウンロード/分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために`trmmdailynrt`フォルダが作成されるディレクトリ。デフォルトは`homedir()`によって呼び出されるホームディレクトリです。

`npd`の以下のフィールドは固定されます。

  * `ID` : trmmdailynrt
  * `name` : 近リアルタイムTRMM日次
  * `doi`   : 10.5067/TRMM/TMPA/DAY-E/7
  * `hroot` : https://disc2.gesdisc.eosdis.nasa.gov/opendap/TRMM*RT/TRMM*3B42RT_Daily.7
  * `fpref` : 3B42RT_Daily
  * `fsuff` : 7.nc4

```
