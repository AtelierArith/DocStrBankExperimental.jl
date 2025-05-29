```
TRMMDaily(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: TRMMDaily{ST,DT}
```

`TRMMDaily`データセット`npd`を作成し、日次出力の最終後処理実行からデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード/分析が始まる日付
  * `stop` : データセットのダウンロード/分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために`trmmdaily`フォルダが作成されるディレクトリ、デフォルトは`homedir()`によって呼び出されるホームディレクトリです。

`npd`の以下のフィールドは固定されます。

  * `ID` : trmmdaily
  * `name` : 最終TRMM日次
  * `doi` : 10.5067/TRMM/TMPA/DAY/7
  * `hroot` : https://disc2.gesdisc.eosdis.nasa.gov/opendap/TRMM*L3/TRMM*3B42_Daily.7
  * `fpref` : 3B42_Daily
  * `fsuff` : 7.nc4

```
