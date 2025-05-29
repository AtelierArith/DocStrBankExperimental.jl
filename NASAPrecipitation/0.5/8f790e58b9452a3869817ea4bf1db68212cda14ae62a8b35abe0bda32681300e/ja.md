```
IMERGMonthly(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: IMERGMonthly{ST,DT}
```

`IMERGMonthly` データセット `npd` を作成して、月次出力のデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード / 分析が始まる日付
  * `stop` : データセットのダウンロード / 分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために `imergmonthly` フォルダが作成されるディレクトリ。デフォルトは `homedir()` によって呼び出されるホームディレクトリです。

`npd` の以下のフィールドは固定されます。

  * `ID` : imergmonthly
  * `name` : IMERG Monthly
  * `doi` : 10.5067/GPM/IMERG/3B-MONTH/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGM.06
  * `fpref` : 3B-MO.MS.MRG.3IMERG
  * `fsuff` : V06B.HDF5
