```
TRMMMonthly(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: TRMMMonthly{ST,DT}
```

`TRMMMonthly`データセット`npd`を作成し、月次出力の最終後処理実行からデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード/分析が始まる日付
  * `stop` : データセットのダウンロード/分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために`trmmmonthly`フォルダが作成されるディレクトリ、デフォルトは`homedir()`によって呼び出されるホームディレクトリです。

`npd`内の以下のフィールドは固定されます:

  * `ID` : trmmmonthly
  * `name` : TRMM Monthly (TMPA 3B43)
  * `doi` : 10.5067/TRMM/TMPA/MONTH/7
  * `hroot` : https://disc2.gesdisc.eosdis.nasa.gov/opendap/TRMM*L3/TRMM*3B43.7
  * `fpref` : 3B43
  * `fsuff` : 7.HDF

```
